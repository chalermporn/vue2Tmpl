<template>
  <header class="nav-bar">
    <el-menu mode="horizontal" :router="true" :default-active="activeIndex" :class="{'login-status': $store.state.token}">
      <el-menu-item index="/home">首页</el-menu-item>
      <el-menu-item index="/list">列表</el-menu-item>
      <el-menu-item index="/table">表格</el-menu-item>
    </el-menu>
    <div class="login-user" v-if="$store.state.token">
      Hello, {{ $store.state.user.userName }}!
      <el-button size="mini" type="text" @click="logOut">log out</el-button>
    </div>
  </header>
</template>

<script>
export default {
  data () {
    return {
      activeIndex: ''
    }
  },
  watch: {
    '$route' () {
      this.activeIndex = this.$route.path
    }
  },
  methods: {
    logOut () {
      this.$store.commit('logout')
      this.$router.push('/home')
    }
  }
}
</script>
