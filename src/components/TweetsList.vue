<template>
  <div>
    <select v-model="sortBy">
      <option value="date">Sort by date</option>
      <option value="likes">Sort by like</option>
    </select>
    <ul class="tweets__wrapper">
      <TweetsListItem v-for="item in sortedItems" :key="item.id" :item="item"/>
    </ul>
  </div>
</template>

<script>
import { ref, computed } from 'vue';

import TweetsListItem from '@/components/TweetsListItem';

export default {
  components: {
    TweetsListItem,
  },
  props: {
    items: {
      type: Array,
      default: [],
    }
  },
  setup ({ items }) {
    const sortBy = ref('date');

    const sortedItems = computed(() => {
      return items.sort((a, b) => {
        if (a[sortBy.value] > b[sortBy.value]) return -1;
        if (a[sortBy.value] < b[sortBy.value]) return 1;
      });
    });

    return {
      sortBy,
      sortedItems,
    }
  }
}
</script>
