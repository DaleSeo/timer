<template>
  <div id="app" class="ui segment pushable">
    <div class="ui inverted vertical icon labeled menu visible thin sidebar">
      <router-link class="item" to="/">
        <i class="home icon"/>Home
      </router-link>
      <router-link class="item" to="/todos">
        <i class="tasks icon"/>Todos
      </router-link>
      <router-link class="item" to="/bookmarks">
        <i class="bookmark icon"/>Bookmarks
      </router-link>
      <router-link class="item" to="/schedule">
        <i class="checked calendar icon"/>Schedule
      </router-link>
    </div>
    <div class="pusher">
      <div class="ui basic segment">
        <div class="ui icon button" @click="toggleMenu">
          <i class="sidebar icon"/>
        </div>
        <Home v-show="atHome"/>
        <router-view v-show="!atHome"></router-view>
      </div>
    </div>
  </div>
</template>

<script>
import Home from './home/Index.vue'

export default {
  components: {Home},
  computed: {
    atHome () {
      return this.$route.path === '/'
    }
  },
  created () {
    Notification.requestPermission()
  },
  mounted () {
    $('#app .ui.sidebar')
      .sidebar({
        context: $('#app')
      })
      // .sidebar('attach events', '#app .menu .item')
  },
  methods: {
    toggleMenu () {
      $('#app .ui.sidebar')
        .sidebar('toggle')
    }
  }
}
</script>

<style>
</style>
