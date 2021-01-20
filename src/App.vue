<template>
  <div id="app">
    <span>父组件</span><br />
    <div>
      <span>好久不见！</span>
    </div>
    <hr />
    <Comp1></Comp1>
  </div>
</template>

<script>
import Comp1 from "./folder/Comp1.vue";
export default {
  name: "app",
  data() {
    return {};
  },
  components: {
    Comp1,
  },
  methods: {},
};
</script>

<style>
</style>
