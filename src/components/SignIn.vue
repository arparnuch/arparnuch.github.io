<template>
  <div class="sign-in">
    <h3>SignIn</h3>
    <div class="block">
      <img src="../assets/girl.png" class="image img-circle">
      <div class="login_section"><el-input placeholder="email" v-model="email"></el-input></div>
      <div class="login_section"><el-input placeholder="password" type="password" v-model="password" @keyup.enter.native="login"></el-input></div>
      <div class="login_section"><el-button :plain="true" type="info" @click.native="login">Login</el-button></div>
    </div>
  </div>
</template>

<script>
import UsersApi from '../api/users.js'
import router from '../router'
export default {
  name: 'sign-in',
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    login () {
      console.log('methods.login')
      UsersApi.login(this.email, this.password, function (_response) {
        // NOTE: Posts.index is not yet implemented
        router.push({ name: 'Posts.index' })
      })
    }
  }
}
</script>

<style scoped>
.el-input {
  width: 300px;

}
.login_section {
  margin-top: 10px;
}

.time {
  font-size: 13px;
  color: #999;
}

.bottom {
  margin-top: 13px;
  line-height: 12px;
}

.button {
  padding: 0;
  float: right;
}

.image {
  max-width: 300px !important;
}

.img-circle {
    border-radius: 50%;
}


</style>
