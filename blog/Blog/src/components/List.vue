//List.vue
<template>
  <div class="container mt-4">
    <div
      class="card shadow-sm p-4 mb-3"
      v-for="(blog, index) in blogs"
      :key="index"
    >
      <h3 @click="$router.push('/detail/' + index)" class="fw-bold">{{ blog.title }}</h3>
      <hr>
      <p class="text-muted">{{ blog.content }}</p>
      <small class="text-secondary">📅 {{ blog.date }}</small>

      <div class="mt-3">
        <button class="btn btn-primary btn-sm">상세보기</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'List',
  props: {
    blogs: Array,
  },
}
</script>