<template>
  <v-app class="flex">
    <navdraw/>
    <v-main>
      <router-view style="background:#121212; height:100%;"></router-view>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue'
import navdraw from './components/navdraw.vue'
export default Vue.extend({
  components: {
    navdraw
  },
  data: function() {
    return {

    }
  }
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
::-webkit-scrollbar {
  height:10px;
  width:5px;
  border-radius:10px; 
  background:rgba(255, 255, 255, 0.2);
}

::-webkit-scrollbar-thumb {
  background:rgba(255, 255, 255, 0.1);
  border-radius:20px;
}
</style>
