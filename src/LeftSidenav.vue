<template lang="html">
    <!--v-if="$store.getters.loggedIn"-->
  <div class="" v-if="$store.getters.loggedIn">
    <el-menu class="el-menu-demo" mode="horizontal">
      <router-link :to="{ name: 'Posts.index'}">
        <el-menu-item index="1"><i class="el-icon-menu"></i>Home</el-menu-item>
      </router-link>
      <router-link :to="{ name: 'Posts.new'}">
      <el-menu-item index="2"><i class="el-icon-plus"></i>New Post</el-menu-item>
      </router-link>

      <el-menu-item index="3" @click.native="logout"><i class="el-icon-setting"></i>Logout</el-menu-item>

    </el-menu>
  </div>

</template>

<script>
import UsersApi from './api/users.js'
export default {
  methods: {
    toggleLeftSidenav () {
      this.$refs.leftSidenav.toggle()
    },
    logout () {
      console.log('methods.logout')
      UsersApi.logout(() => {

      })
    }
  }
}
</script>

<style lang="css">

.el-menu-item{
  /*position: absolute;*/
  /*top: 50px;*/
  float: right;
}
</style>
