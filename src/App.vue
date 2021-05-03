<template>
  <ToggleButtonGrid
      :numberOfToggleButtonColumns="8"
      :numberOfToggleButtonRows="3"
      @onChange="onChange($event)"
  />
</template>

<script>

  import ToggleButtonGrid from './components/ToggleButtonGrid.vue';

  export default {
    name: 'App',
    components: {
      ToggleButtonGrid
    },
    methods: {
      onChange(event) {
        console.log(`App| received onChange-event from child`);
        console.log(event);
      }
    }
  }
</script>

<style>

</style>
