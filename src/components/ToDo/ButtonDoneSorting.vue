<template>
  <v-btn
  @click="$store.commit('toggleSorting')"
  class="button-done-sorting"
  color="primary">
      Done Sorting
  </v-btn>
</template>

<script>
export default {

}
</script>

<style lang="sass">
    .button-done-sorting
        position:fixed
        bottom: 5px
        left: 50%
        transform: translateX(-50%)
</style>