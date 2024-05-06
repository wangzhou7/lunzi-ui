<script lang="ts">
import { ref, provide } from "vue"
import { router } from './router'

export default {
  name: 'App',
  setup() {
    const width = document.documentElement.clientWidth
    const visible = ref(width <= 500 ? false : true)
    provide("menuvisible", visible);// set
    router.afterEach(()=>{
      if(width<=500){
        visible.value = false;
      }
    })
  }
}
</script>




<template>
  <router-view />
</template>

