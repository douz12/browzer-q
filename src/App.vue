<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">
    <q-layout ref="layout" view="lHh Lpr lFf">
      <router-view></router-view>
      <q-tabs slot="footer" position="bottom" color="red-12">
        <q-route-tab
          icon="home"
          to="/"
          exact
          slot="title"
        />
        <q-route-tab
          icon="camera"
          to="/camera"
          exact
          slot="title"
        />
        <q-route-tab
          icon="notifications"
          to="/notifications"
          exact
          slot="title"
        />
      </q-tabs>
    </q-layout>
  </div>
</template>

<script>
import { QTabs, QRouteTab, QLayout, QBtn, QIcon } from 'quasar'
/*
 * Root component
 */
export default {
  components: {
    QTabs, QRouteTab, QLayout, QBtn, QIcon
  }
}
</script>

<style lang="stylus">
@import '~variables'

</style>
