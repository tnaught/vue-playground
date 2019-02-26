<template>
  <nav>
    <span class="nav-item" v-for="(tab, index) in tabs" v-bind:key="index" v-bind:class="{active: tab==_current}" @click="clickHandler(tab)">{{tab}}</span>
  </nav>
</template>

<script>
export default {
  name: 'NavTab',
  props: {
    tabs: Array,
    current: String,
  },
  computed: {
    _current: function() {
      if (this.tabs.indexOf(this.current) > -1) {
        return this.current;
      }
      return this.tabs[0]
    }
  },
  methods: {
    clickHandler: function(tab) {
      this.$emit('tab-change', tab);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.nav-item {
  padding: 5px 16px;
  margin-left: -1px;
  border: 1px solid #a4a4a4;
}
.nav-item:first-child {
  margin-left: 0;
}
.nav-item.active {
  color: #f90a12;
}
</style>
