<template>
  <div id="app">
    <!-- <qyh-Button :size="size" :width="100" :height="40" :plain ='plain' :round='round' :circle='circle' :loading='loading'
    :disabled='disabled'
    @click='clickHandle' 
    ></qyh-Button> -->

    <!-- <qyh-input :type='type' v-model='value' 
    :max='max'
    :min='min'
    :maxlength='maxlength'
    @blur='blurHandle'
    :disabled='true'
    /> -->

    <qyh-radio v-model="radio" label="1">男</qyh-radio>
    <qyh-radio v-model="radio" label="2">女</qyh-radio>

  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import qyhButton from "./components/Button.vue";
import qyhInput from "./components/Input.vue"
import qyhRadio from "./components/radio.vue"

@Component({
  components: {
    qyhButton,
    qyhInput,
    qyhRadio
  },
})
export default class App extends Vue {
  type='textarea'
  value=''
  min=1
  max=10
  maxlength=10
  radio = 1

  clickHandle(e:Event) {
    console.log('点击事件', e);
  }
  blurHandle(e:Event) {
    console.log('blur', e);
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
