<template>
<br>
  <h1>Sélectionnez vos catégories favorites </h1>

  <selection-box 
    :selection="selection"
  >
  </selection-box>

<div class="rp" style="display: flex; flex-wrap: wrap;">
  <player-card
    v-for="(player, index) in playersData.players"
    :key="index"
    :player="player"
    :player-index="index"
    @add-player="addPlayerToSelection"
    @delete-player="deletePlayerToSelection"
    @update-counter="updateCounter"
    >
  </player-card>
</div>
</template>

<script>
import playersData from '../assets/data/players.json'
import PlayerCard from './PlayerCard.vue'
import SelectionBox from './SelectionBox.vue'

export default {
  name: "player-List",
  components: {
    PlayerCard,
    SelectionBox
  },
  data() {
    return {
      playersData : playersData,
      counter : null,
      selection: []
    }
  },
  methods: {
    addPlayerToSelection(player) {
      this.selection.push(player)
      this.$emit('update-selection', player)
      this.$emit('update-counter', player)
    },
    deletePlayerToSelection(index) {
      this.selection.splice(index, 1)
      this.$emit('delete-selection', index)
      console.log(index)
    },
    updateCounter(isClicked) {
         if (isClicked) {
        this.counter++
      } else {
        this.counter--
      }
    }
  }
}




</script>

<style>

</style>