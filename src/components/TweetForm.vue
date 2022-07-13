<template>
  <form @submit.prevent="onSubmit">
    <textarea
      v-model="body"
      required
      placeholder="Type tweet here"
    ></textarea>
    <br>
    <button class="btn btnTweet" type="submit">Post Tweet</button>
  </form>
</template>

<script>
import { ref } from 'vue';

export default {
  emits: [
    'onSubmit'
  ],
  setup (_, { emit }) {
    const body = ref('');

    const onSubmit = (e) => {
      emit(
        'onSubmit',
        {
          avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
          body: body.value,
          likes: 0,
          date: new Date(Date.now()).toLocaleString(),
        }
      );
      // reset
      body.value = "";
    };

    return {
      body,
      onSubmit,
    }
  }
}
</script>
