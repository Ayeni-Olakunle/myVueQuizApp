<template>
  <div id="app">
    <div id="nav">
      <div class="h1 mb-0 holdL">
        <p @click="hasHistory()? $router.go(-1) : $router.push('/')" class="back"><b-icon-arrow-left-circle></b-icon-arrow-left-circle></p>
        <p class="home"><router-link to="/">Home</router-link></p>
      </div>
      <!-- <router-link to="/about">About</router-link> -->
      <h2 class="ComPName">
        <router-link to="/">Diamond Plus Quiz App</router-link>
      </h2>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'app',
  methods: {
  hasHistory () { return window.history.length > 2 }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #42b983;
  text-decoration: none;
}

/* #nav a.router-link-exact-active {
  color: #42b983;
} */

.holdL{
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.home{
  font-size: 20px;
}

.ComPName{
  text-align: center;
  margin-top: 20px;
}

.back{
  color: #42b983;
}
</style>
