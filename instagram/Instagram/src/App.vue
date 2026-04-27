<template>
  <div>
    <div class="header">
      <ul class="header-button-left">
        <li v-on:click="step=0" v-if="step > 0">Cancel</li>
      </ul>
      <ul class="header-button-right">
        <li v-on:click="step++" v-if="0 < step && step < 2">Next</li>
        <li v-on:click="publish" v-if ="step >= 2">발행</li>
      </ul>
      <img src="./assets/logo.svg" class="logo" />
    </div>

    <Container :posts="posts" :step="step" :image="image" @content="content = $event"/>
    <button @click="more" v-if="step == 0">더보기</button>

    <div class="footer" v-if="step == 0">
      <ul class="footer-button-plus">
        <input @change="upload" multiple accept="image/*" type="file" id="file" class="inputfile" />
        <label for="file" class="input-plus">+</label>
      </ul>
    </div>
  </div>
</template>

<script>
import Container from './components/Container.vue';
import posts from './assets/post.js';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Container
  },
  data() {
    return {
      step:0,
      moreCount: 0,
      posts,
      image : '',
      content : ''
    };
  },
  methods: {
    more() {
      const url = `https://qkrwpgus.github.io/vue/more${this.moreCount}.json`;
      axios.get(url).then((result) => {
        this.posts.push(...result.data);
        this.moreCount += 1;
      });
    },

  upload(e){
      let 파일 = e.target.files;
      console.log(파일);
      console.log(파일[0]);
      let url = URL.createObjectURL(파일[0]);
      console.log(url);
      this.image = url;
      this.step=1;
    },
  publish() {
      console.log('publish called');
      console.log('image:', this.image);
      console.log('content:', this.content);
      var 내게시물 = {
        name: "Kim Hyun",
        userImage: "https://picsum.photos/100?random=3",
        postImage: this.image,
        likes: 0,
        date: new Date().toLocaleDateString(),
        liked: false,
        content: this.content,
        filter: ""
      };
      console.log('새 게시물:', 내게시물);
      this.posts.unshift(내게시물);
      console.log('posts length:', this.posts.length);
      this.step = 0;
    }
  }
};
</script>

<style lang="css">
@import './assets/main.css';
</style>