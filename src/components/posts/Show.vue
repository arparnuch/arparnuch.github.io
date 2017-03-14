<template>
  <div class="post">
    <div class="">
      <iccs340-post :post='post'></iccs340-post>
      <div style="margin-bottom:580px;"></div>
      <div class="" >
        <div v-for="comment in comments" :key="comment.id">
          <iccs340-comment :comment='comment'></iccs340-comment>
        </div>
      </div>
      <iccs340-new-comment :post='post'></iccs340-new-comment>
    </div>
  </div>
</template>

<script>
import PostsApi from '../../api/posts.js'
import CommentsApi from '../../api/comments.js'

export default {
  name: 'post',
  components: {
    Iccs340Post: require('./Post_card'),
    Iccs340Comment: require('../comments/Comment'),
    Iccs340NewComment: require('../comments/New')
  },
  data () {
    return {
      post: {},
      comments: [],
      error: null
    }
  },
  created () {
    // fetch the data when the view is created and the data is
    // already being observed
    this.fetchData()
  },
  watch: {
    // call again the method if the route changes
    '$route': 'fetchData'
  },
  methods: {
    fetchData () {
      PostsApi.getPost(this.$route.params.id, _post => {
        this.post = _post
        CommentsApi.getComments(_post.id, _comments => {
          this.comments = _comments
        })
      })
    }
  }
}
</script>

<style scoped>

</style>
