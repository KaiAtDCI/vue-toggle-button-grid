<!-- ToDo: Check how label for="" can be implemented -->
<!-- ToDo: Check if component can provide controlled/uncontrolled behaviour at same time -->

<template>
    <div class="toggle-button"
         :style="inlineStyle"
         @click="onclick()"
    />
</template>

<script>

  export default {

    name: 'ToggleButton',

    props: {
      id: Number,
      initialValue: {
        type: Boolean,
        default: false,
      }
    },

    data() {
      return {
        value: this.initialValue,
      }
    },

    created() {
      this.emitValue();
    },

    computed: {
      inlineStyle() {
        const color = this.value ? "lightsteelblue" : "lightgray";
        return "background-color: " + color;
        // Todo: Why does using class-binding and styling class not work?!
      }
    },

    methods: {
      onclick() {
        this.value = !this.value;
        this.emitValue();
      },
      emitValue() {
        this.$emit('onChange', this.value);
      }
    }
  }
</script>

<style scoped>
  .toggle-button {
    display: inline-flex;
    align-items: center;
    width: 1em;
    height: 1em;
    padding: 0;
    margin: 0;
    background-color: lightgray;
  }
</style>
