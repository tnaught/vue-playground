<template>
  <div id="app">
    <NavTab :tabs="tabs" :current="currentTab" @tab-change="tabChangeHandler"></NavTab>
    <component :is="tabContentComponent">
      <h3>欢迎来到{{currentTab}}</h3>
    </component>
  </div>
</template>

<script>
import NavTab from './components/NavTab.vue'
import GameTab from './components/GameTab.vue'
import BookTab from './components/BookTab.vue'
import VedioTab from './components/VedioTab.vue'

export default {
  name: 'app',
  components: {
    NavTab,
    GameTab,
    BookTab,
    VedioTab,
  },
  data: function() {
    return {
      tabs: ['游戏', '小说', '视频'],
      currentTab: '小说',
    }
  },
  computed: {
    tabContentComponent: function() {
      switch (this.currentTab) {
        case '游戏':
          return GameTab;
        case '小说':
          return BookTab;
        case '视频':
          return VedioTab;
        default:
          return GameTab;
      }
    }
  },
  methods: {
    tabChangeHandler: function(tab) {
      this.currentTab = tab;
    }
  },
  created: function() {

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
