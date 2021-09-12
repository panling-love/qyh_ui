<template>
  <div id="app">
    <qyh-Button :size="size" :width="100" :height="40" :plain ='plain' :round='round' :circle='circle' :loading='loading'
    :disabled='disabled'
    @click='clickHandle' 
    ></qyh-Button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import qyhButton from "./components/Button.vue";

@Component({
  components: {
    qyhButton,
  },
})
export default class App extends Vue {
  size = 'medium';
  height = '200px';
  type = 'success';
  plain = true;
  round = true;
  circle = true;
  loading = true;
  disabled = true;

  clickHandle(e:Event) {
    console.log('点击事件', e);
  }
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
