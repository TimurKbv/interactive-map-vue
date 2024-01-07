<script setup >
  import { defineComponent } from 'vue';  
  import AppHeader from './components/AppHeader.vue';
  import AppNavBar from './components/AppNavBar.vue';
  import MainMap from './components/MainMap.vue';
  import AppFooter from './components/AppFooter.vue';
</script>


<template>
    <div class="grid grid-cols-8 grid-rows-12 w-screen h-screen bg-gray-400">
      <AppHeader/>
      <AppNavBar />
      <MainMap />
      <AppFooter />

    </div>
</template>



