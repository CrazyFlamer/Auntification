<template>
  <div id="app">
    <div id="nav">
      <router-link v-if="user == ''" to="/login">Login</router-link>
      <router-link v-else :to="`/users/${user.login}}`">{{user.name}}</router-link> |
    </div>
    <router-view :user='user' @auth = "authStart" />
  </div>
</template>

<script>
export default {
  data(){
    return{
      user: '',
    }
  },
  methods: {
    authStart($data){
      this.user = $data;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}
#nav a {
  font-weight: bold;
  color: #2c3e50;
}
#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
