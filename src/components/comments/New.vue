<template>
  <div class="new-post" style="margin-top:50px;">
      <el-card :body-style="{ padding: '0px' }" class="centered">
        <div class="" style="padding: 18px;">
          <div>
            <div style="margin-bottom:10px;">
              <i style="margin-right:5px;"class="el-icon-edit"></i>
              <label>Add Comment</label>
            </div>
            <el-input type="textarea" :autosize="{ minRows: 4, maxRows: 4, minColumns: 10}"
            placeholder="Type your comment here" v-model="comment.content">
            </el-input>
          </div>
          <span style="flex: 1"></span>
          <el-button :plain="true" type="success" @click.native="createComment" style="margin-top:10px;">Save</el-button>
          <span style="flex: 1"></span>
        </div>
    </el-card>
  </div>
</template>

<script>
import CommentsApi from '../../api/comments.js'
import router from '../../router'

export default {
  name: 'new-comment',
  data () {
    return {
      comment: {
        content: ''
      }
    }
  },
  props: {
    post: {
      type: Object,
      required: false,
      default: {}
    }
  },
  methods: {
    createComment () {
      var postId = this.post.id
      var content = this.comment.content
      this.comment.content = ''
      CommentsApi.createComment(postId, content,
        function (_comment) {
          console.log(_comment)
          router.push({ name: 'Posts.show', params: { post_id: postId }, query: { t: new Date() } })
        }
      )
    }
  }
}
</script>

<style scoped>
.md-list-item {
  padding-left: 40px;
}

.el-card{
  width:700px;
}


.el-textarea {
  width: 30% !important;
}

.centered {
  position: relative;
  top: 40%;
  left: 50%;
  /* bring your own prefixes */
  transform: translate(-50%, -50%);
}


.el-textarea[data-v-7122c0b0] {
  width: 400px !important;

}

</style>
