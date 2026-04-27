//Detail.vue
<template>
  <div class="container mt-4">
    <div class="card shadow-sm p-4">
      <h4 class="text-muted mb-3">상세페이지</h4>
      <h5 class="fw-bold">{{ blogs[$route.params.id].title }}</h5>
      <hr>
      <p>{{ blogs[$route.params.id].content }}</p>
      <button class="btn btn-secondary"">
        ← 뒤로가기
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Detail',
  props: {
    blogs: Array,
  },
}
</script>