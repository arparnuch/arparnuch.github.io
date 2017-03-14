<template>
  <div class="post">
    <div>
      <span>Post Name : {{ post.name }}</span>
      <p>Content : {{ post.content }}</p>
    </div>
  </div>
</template>

<script>

export default {
  name: 'post',
  props: {
    post: {
      type: Object,
      required: false,
      default: {}
    }
  }
}
</script>

<style scoped>

</style>
