<template>
  
  <div  @click="addToSelection(playerIndex)"
    style="flex-grow: 3; min-width: 500px; cursor: pointer;" 
    class="border border-orange-900 m-2 p-2 rounded flex justify-between"
    :class="{ 'secondecolor': isClicked, 'firstcolor': !isClicked}"
  >
    <div>
      <h3 class="text-lg font-bold">{{ playerName }} ({{ player.number }})</h3>
      <p>{{ player.position }}</p>
      
    </div>
    
   
  </div>
</template>

<script>
export default {
  name: "player-card",
  props: ['player', 'player-index'],
  data() {
    return {
      isClicked : false,

    }
  },
  computed: {
    playerName() {
      if(this.player.name.split('.').length > 1){
        return this.player.name.split('.')[1]
      }
      return this.player.name;
    }
    /*playerInjured() {
      if(this.player.health == "out"){
        return true
      }
      return false
    },*/
 /*   isInjuredClass() {
      return { 
        'bg-yellow-500': this.playerInjured, 
        'bg-orange-500': !this.playerInjured 
        }
    },*/
  },
  methods: {
    addToSelection(index) {
      
      this.isClicked = !this.isClicked
      if (this.isClicked) {
        this.$emit('add-player', this.player)
      } else {
        this.$emit('delete-player', index)

      }
    //  this.$emit('update-counter', this.isClicked)

  }
  }
}



</script>

<style scoped>

</style>