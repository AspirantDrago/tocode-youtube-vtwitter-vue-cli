<template>
  <div class="wrapper">
    <!-- header -->
    <div class="wrapper-content">
      <div class="view">
        <div class="container">
          <TweetForm @onSubmit="handleSubmit" />
          <TweetsList :items="items"/>
        </div>
      </div>
    </div>
    <!-- footer -->
  </div>
</template>

<script>
import { ref } from 'vue';

import TweetsList from '@/components/TweetsList';
import TweetForm from './components/TweetForm.vue';

export default {
  components: {
    TweetForm,
    TweetsList
  },
  setup () {
    const items = ref([
      {
        id: 1,
        avatar: `https://avatars.dicebear.com/api/male/1.svg`,
        body: 'hello vue 3',
        likes: 12,
        date: new Date(Date.now()).toLocaleString(),
      },
      {
        id: 2,
        avatar: `https://avatars.dicebear.com/api/male/2.svg`,
        body: 'hello world',
        likes: 6,
        date: new Date(Date.now()).toLocaleString(),
      },
    ]);

    const handleSubmit = (item) => {
      item.id = items.value.length + 1;
      items.value.push(item);
    }

    return {
      items,
      handleSubmit,
    }
  }
}
</script>
