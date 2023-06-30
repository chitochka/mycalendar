

<template>
  <v-app id="inspire">
    <!-- <v-navigation-drawer v-model="drawer"></v-navigation-drawer> -->

    <v-app-bar>
      <!-- <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon> -->
      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <HelloWorld v-show="false"></HelloWorld>
      <!-- <hr/> -->
      <Diar :smeny="smeny" class="diar"></Diar>
      <!-- <v-divider :thickness="3" color="success"></v-divider> -->
      <!-- <br/> -->
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref } from 'vue'
  const drawer = ref(null)
  
</script>

<script>
import HelloWorld from './components/HelloWorld.vue';
import Diar from './components/Diar.vue';

  export default {
    data: () => ({ 
      drawer: null,
      file:null,
      smeny: [
        {"1":"alex"},{},{},
        {},{},
        {
          "1":"alex",
          "2":"Anna"
      },
        {},{},{},
        {},{},{}
      ]
    }),
    components:{HelloWorld,Diar}
  }
</script>

<style scoped>

</style>
