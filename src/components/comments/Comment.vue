<template>
  <div class="comment" style="margin-top:10px;">
    <el-card :body-style="{ padding: '0px' }" class="centered">
      <div style="padding: 10px;">
        <i style="margin-top:10px; "class="el-icon-message"></i>
      </div>
      <div style="padding: 14px;">
        <span>Comment</span>
        <p>Email: {{ comment.user.email }}</p>
        <p>Content: {{ comment.content }}</p>
      </div>
    </el-card>
  </div>
</template>

<script>

export default {
  name: 'comment',
  props: {
    comment: {
      type: Object,
      required: false,
      default: {}
    }
  }
}
</script>

<style scoped>
.el-card{
  width:500px;
}

.centered {
  position: relative;
  top: 40%;
  left: 50%;
  /* bring your own prefixes */
  transform: translate(-50%, -50%);
}



</style>
