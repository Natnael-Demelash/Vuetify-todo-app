<template>
  <v-app app id="app">
   <Navbar />
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import Navbar from '../src/components/Navbar.vue'
export default {
  name: 'App',
  components:{Navbar},
  data: () => ({
    //
  }),
};
</script>

<style>
#app {
    background-color: rgba(211, 211, 211, 0.425);
}
</style>
