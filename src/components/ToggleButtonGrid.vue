<template>
  <div class="toggle-button-grid">
    <ToggleButtonGrid
        v-for="(ToggleButtonGridNumber, index) in numberOfToggleButtonColumns"
        :key="ToggleButtonGridNumber"
        :numberOfToggleButtons="numberOfToggleButtonRows"
        @onChange="onChange($event, index)"
    >
    </ToggleButtonGrid>
  </div>
</template>

<script>
  import ToggleButtonGrid from "./ToggleButtonColumn";

  export default {

    name: 'ToggleButtonPane',

    components: {
      ToggleButtonGrid
    },

    props: {
      numberOfToggleButtonColumns: {
        type: Number,
        default: 16,
      },
      numberOfToggleButtonRows: {
        type: Number,
        default: 3,
      }
    },

    emits: ['onChange'],

    data() {
      return {
        value: [], // new Array(this.numberOfToggleButtonColumns),
      }
    },

    methods: {
      onChange(event, index) {
        this.value.splice(index,1, event);
        this.emitValue();
      },
      emitValue() {
        this.$emit('onChange', this.value);
      }
    },
  }
</script>

<style scoped>
  .toggle-button-grid {
    display: flex;
    flex-direction: row;
    gap: .125em;
    color: black;
  }
</style>
