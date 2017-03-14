<template>
  <div class="post-card">
    <el-card :body-style="{ padding: '0px' }" class="centered">
      <img src="../../assets/cat.png">
      <div style="padding: 14px;">
        <span>Post Name : {{ post.name }}</span>
        <p>Content : {{ post.content }}</p>
      </div>
    </el-card>
  </div>
</template>
<script>
export default {
  name: 'post-card',
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
.el-card{
  width:1000px;
}

.centered {
  position: absolute;
  top: 40%;
  left: 50%;
  /* bring your own prefixes */
  transform: translate(-50%, -50%);
}
</style>
