<template>
  <nav class="navbar navbar-light bg-light px-3">
    <span class="navbar-brand fw-bold">Vuelog</span>
  </nav>

  <router-view :blogs="블로그글"></router-view> 

</template>

<script>
import data from './assets/blog';

export default {
  name: 'App',
  data() {
    return {
      블로그글: data,
    }
  }
}
</script>