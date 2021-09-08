<template>
  <div id="app">
    <Button :size="size" :width="100" :height="height"></Button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Button from "./components/Button.vue";

@Component({
  components: {
    Button,
  },
})
export default class App extends Vue {
  size = 'medium';
  height = '200px'
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
