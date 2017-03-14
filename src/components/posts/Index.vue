<template>
  <div class="posts">
    <h1>All posts</h1>
    <el-table :data="posts" border style="width: 100%">
       <el-table-column prop="" label="" width="200">
         <template scope="img">
           <img src="../../assets/cat.png" style="width:50%;">
         </template>
       </el-table-column>
      <el-table-column label="Post Name-Detail" width="1001">
        <template scope="scope">
          <router-link :to="{ name: 'Posts.show', params: {id: scope.row.id } }" style="color:black;">
            <iccs340-post :post='scope.row'></iccs340-post>
          </router-link>
        </template>
      </el-table-column>
     <el-table-column prop="img1" label="" width="200">
       <template scope="image">
         <i class="el-icon-information"></i>
       </template>
     </el-table-column>
   </el-table>
  </div>
</template>

<script>
import PostsApi from '../../api/posts.js'

export default {
  name: 'posts',
  data () {
    return {
      posts: null,
      error: null,
      tableData: []
    }
  },
  components: {
    Iccs340Post: require('./Post')
  },
  beforeRouteEnter (to, from, _next) {
    PostsApi.getPosts(_posts => {
      _next(vm => {
        vm.posts = _posts
      })
    })
  },
  watch: {
    $route () {
      PostsApi.getPosts(_posts => {
        this.posts = _posts
      })
    }
  }
}
</script>

<style scoped>
.posts {
  padding: 0 10px;
  /*margin-left: -110px;*/
}

td{
  text-align: left !important;
}
</style>
