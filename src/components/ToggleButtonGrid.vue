<template>
  <div class="toggle-button-grid">
    <ToggleButtonColumn
        v-for="(toggleButtonColumnNumber, index) in numberOfToggleButtonColumns"
        :key="toggleButtonColumnNumber"
        :numberOfToggleButtons="numberOfToggleButtonRows"
        :class="{highlighted: highlightedColumnNumber === index}"
        @onChange="onChange($event, index)"
    >
    </ToggleButtonColumn>
  </div>
</template>

<script>
  import ToggleButtonColumn from "./ToggleButtonColumn";

  export default {

    name: 'ToggleButtonGrid',

    components: {
      ToggleButtonColumn
    },

    props: {
      numberOfToggleButtonColumns: {
        type: Number,
        default: 16,
      },
      numberOfToggleButtonRows: {
        type: Number,
        default: 3,
      },
      highlightedColumnNumber: {
        type: Number,
        default: 0,
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
  .highlighted {
    box-shadow: 0 0 2px 2px red;
    background-color: red;
  }

</style>
