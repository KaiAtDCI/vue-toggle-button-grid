<template>
  <ToggleButtonMatrix
      :numberOfToggleButtonColumns="8"
      :numberOfToggleButtonRows="3"
      @onChange="onChange($event)"
  />
</template>

<script>

  import ToggleButtonMatrix from './components/ToggleButtonGrid.vue';

  export default {
    name: 'App',
    components: {
      ToggleButtonMatrix
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
