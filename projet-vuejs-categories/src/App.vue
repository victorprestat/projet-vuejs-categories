<template>
  <nav-bar
    @change-component="updateSelectedComponent"
  ></nav-bar>

  <keep-alive>
    <component 
      :is="selectedComponent"
      v-bind="currentProps"
      @update-selection="updateSelection"
    >
    </component>
  </keep-alive>
  
</template>

<script>
import PlayerList from './components/PlayerList.vue'
import SelectionList from './components/SelectionList.vue'

import NavBar from './components/navigation/NavBar.vue'

export default {
  name: 'App',
  components: {
    PlayerList,
    NavBar,
    SelectionList
  },
  data() {
    return {
      selectedComponent: 'player-list',
      selectionArray: []
    }
  },
  computed: {
    currentProps() {
      if(this.selectedComponent == "selection-list") {
        return { selection: this.selectionArray }
      }
      return false
    }
  },
  methods: {
    updateSelectedComponent(comp) {
      this.selectedComponent = comp
    },
    updateSelection(player) {
      this.selectionArray.push(player)
    }
  }
}
</script>
<style>

</style>
