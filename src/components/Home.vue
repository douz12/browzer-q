<template>
  <!-- if you want automatic padding use "layout-padding" class -->
  <q-layout ref="layout" view="lHh Lpr lFf" reveal>
    <q-toolbar color="red-12" slot="header">
      <q-toolbar-title>
        <b>Home</b>
      </q-toolbar-title>
    </q-toolbar>
    <MemoryList />
  </q-layout>
</template>

<script>
import MemoryList from '@/MemoryList.vue'
import { QLayout, QToolbar, QToolbarTitle } from 'quasar'

export default {
  data () {
    return {
    }
  },
  components: {
    QLayout, QToolbar, MemoryList, QToolbarTitle
  }
}
</script>

<style>
</style>
