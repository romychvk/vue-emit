<template>
  <button @click="currentComponentFunction">
    <slot></slot>
  </button>
</template>

<script>
  export default {
    name: "ChildComponent",
    data() {
      return {
        count: 1
      }
    },
    methods: {
      currentComponentFunction(){
        this.$emit("customNamedEmit", "Button clicked " + this.count++ + " times");
      }
    }
  }
</script>

<style scoped>
  button {
    display: block;
    font-size: 1.25rem;
    padding: 5px 15px;
    margin: 2rem auto;
  }
</style>