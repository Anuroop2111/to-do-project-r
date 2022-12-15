<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/>
</template>

<script>
import AboutView from './views/AboutView.vue'

export default ({
//  name : 'AppView',
 components : {AboutView},
  // data () {
  //   return {
  //     show_save_btn : false,
  //           title : "",
  //           task_input_val : "",
  //           task_ : [],
  //           List_ : [
  //               // {title:"",tasks : []} // This is the master List of all newly created lists.
  //           ]
  //   }
  // }

})
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
