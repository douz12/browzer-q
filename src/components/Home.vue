<template>
  <!-- if you want automatic padding use "layout-padding" class -->
  <div class="layout-padding">
    <MemoryList />
  </div>
</template>

<script>
import MemoryList from '@/MemoryList.vue'

export default {
  data () {
    return {
    }
  },
  components: {
    MemoryList
  }
}
</script>

<style>
</style>
