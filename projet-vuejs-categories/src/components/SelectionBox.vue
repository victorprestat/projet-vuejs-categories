<template>
  <div>Nombre de catégories selectionnées : {{ selection.length }}
    <span v-if="nbrJoueurs"></span>
    <span v-else></span>
  </div>
  <br>
</template>

<script>
export default {
  name: "selection-box",
  props: ['selection'],
  computed: {
    nbrJoueurs() {
      if(this.selection > 1){
        return true
      }
      return false
    }
  }
}
</script>

<style>

</style>