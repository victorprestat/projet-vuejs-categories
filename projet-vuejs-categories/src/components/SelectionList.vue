<template>
  <div class="container w-4/5 mx-auto mt-4">
    <h1 class="text-lg font-bold">Mes catégories</h1>

    <div v-if="selection.length == 0">
      <p>Aucune catégorie sélectionnées</p>
    </div>
    <div v-else>
      
      <div style="flex-grow: 3; min-width: 500px; cursor: pointer; background-color: #6ddb48;"
        v-for="player in selection"
        :key="player.name" 
        class="border border-orange-900 m-2 p-2 rounded flex justify-between"
      >
        <h3>{{ player.name }} </h3>
        <span>{{ player.position }}</span>
      </div>

      
    </div>
    
  </div>
  
</template>

<script>
export default {
  name: "selection-list",
  props: ['selection'],
  methods: {
  },
  computed: { 
    total() {
       var total = this.selection.reduce(function(previousValue, currentValue) {
          return previousValue.number + currentValue.number
        });
       return total;
    }
  }
  
}
</script>

<style>
</style>