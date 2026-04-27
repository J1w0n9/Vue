<template>
  <div class="container">
    <Post
      v-for="(post, index) in posts"
      :key="index"
      :post="post"
    />
  </div>
</template>

<script>
import Post from './Post.vue';

export default {
  name: 'Container',
  components: { Post },
  props: {
    posts:  Array,
    }
};
</script>