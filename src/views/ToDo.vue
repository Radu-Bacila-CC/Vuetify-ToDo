<template>
  <div class="home">

  <list-tasks v-if="$store.state.tasks.length"/>
  <no-tasks v-else />
  <button-done-sorting 
  v-if="$store.state.sorting"/>
    </div>
</template>

<script>

  export default {
    name: 'Home',
    components: {
      'list-tasks':require('@/components/ToDo/ListTasks.vue').default,
      'no-tasks':require('@/components/ToDo/NoTasks.vue').default,
      'button-done-sorting':require('@/components/ToDo/ButtonDoneSorting.vue').default,
    }
  }
</script>
<style lang="sass">
  .no-tasks
    position: absolute
    left: 50%
    top: 50%
    transform: translate(-50%, -50%)
    opacity: 0.8
</style>
