<template>
  <div class="toggle-button-column">
    <ToggleButton
        v-for="(toggleButtonNumber, index) in numberOfToggleButtons"
        :key="toggleButtonNumber"
        @onChange="onChange($event, index)"
    >
    </ToggleButton>
  </div>
</template>

<script>
  import ToggleButton from "./ToggleButton";

  export default {

    name: 'ToggleButtonPane',

    components: {
      ToggleButton
    },

    props: {
      numberOfToggleButtons: {
        type: Number,
        default: 4,
      }
    },

    emits: ['onChange'],

    data() {
      return {
        value: new Array(this.numberOfToggleButtons),
      }
    },

    methods: {
      onChange(event, index) {
        console.log(`ToggleButtonStack| received onChange(${event}, ${index})`);
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
  .toggle-button-column {
    display: flex;
    flex-direction: column;
    gap: .125em;
    color: black;
  }
</style>
