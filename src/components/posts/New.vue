<template>
  <div class="new-post" style="margin-top:300px;">
    <el-card :body-style="{ padding: '0px' }" class="centered">
      <div style="margin-top:30px;">
        <h1><i class="el-icon-document" style="margin-right:10px;"></i>New Post</h1>
      </div>
      <div>
        <div ><el-input class="enter_name" placeholder="Enter post name" v-model="post.name"></el-input></div>
        <div style="margin-top:20px;"><el-input class="enter_content" type="textarea"
          :rows="7" placeholder="Content" v-model="post.content"></el-input></div>
      </div>
      <div class="" style="margin-top:20px;">
        <span style="flex: 1"></span>
        <el-button :plain="true" type="success" @click.native="createPost">Save</el-button>
        <span style="flex: 1"></span>
      </div>
    </el-card>
  </div>
</template>

<script>
import PostsApi from '../../api/posts.js'
import router from '../../router'
export default {
  name: 'new-post',
  data () {
    return {
      post: {
        name: '',
        content: ''
      }
    }
  },
  methods: {
    createPost () {
      PostsApi.createPost(this.post,
        function (_post) {
          router.push({ name: 'Posts.index' })
        }
      )
    }
  }
}
</script>

<style scoped>
.el-input{
  width: 500px;
}

.el-card{
  width:800px;
  height: 390px;
}

.centered {
  position: relative;
  top: 40%;
  left: 50%;
  /* bring your own prefixes */
  transform: translate(-50%, -50%);
}
.enter_name{
  width:200px;
  margin-left: -300px;
}

.enter_content {
  width: 500px;
  /*height: 200px;*/
}

</style>
