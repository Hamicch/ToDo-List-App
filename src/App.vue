<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>

export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(219, 146, 160);
}

#nav {
  line-height: 60px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
   text-decoration: none;
}

#nav a.router-link-exact-active {
  color: crimson;
}

button {
  width: 60px;
  height: 30px;
  background-color: crimson;
  color: #fff;
  border: none;
  cursor: pointer;
  border-radius: 4px;
  margin: 5px;
  transition: all 0.3s ease-in-out;
}

button:hover {
  background-color: rgb(220, 20, 60, 0.9);
}
</style>
