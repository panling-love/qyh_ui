<template>
  <label class="qyh-radio" :class="{'is-checked': label == model}">
    <span class="qyh-radio_input">
      <span class="qyh-radio_inner"></span>
      <input
      type="radio"
      class="qyh-radio_original"
      :value="label"
      v-model="model"
      >
    </span>
    <span class="qyh-radio_label">
      <slot></slot>
    </span>
  </label>
</template>
<script lang='ts'>
import { Component, Vue, Prop, Watch } from "vue-property-decorator";

@Component({})
export default class qyhRadio extends Vue {
  name = 'qyhRadio'
  @Prop() label:any;
  @Prop() value?:Number | String;

  get model() {
    return this.value;
  }
  set model(val) {
    this.$emit('input', val);
  }
}
</script>
<style lang="scss" scoped>
  .qyh-radio{
    color: #606266;
    font-weight: 500;
    line-height: 1;
    position: relative;
    cursor: pointer;
    display: inline-block;
    white-space: nowrap;
    outline: none;
    font-size: 14px;
    margin-right: 30px;
    -moz-user-select: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    .qyh-radio_input{
      white-space: nowrap;
      cursor: pointer;
      outline: none;
      display: inline-block;
      line-height: 1;
      position: relative;
      vertical-align: middle;
      .qyh-radio_inner{
        border: 1px solid #dcdfe6;
        border-radius: 100%;
        width: 14px;
        height: 14px;
        background-color: #fff;
        position: relative;
        cursor: pointer;
        display: inline-block;
        box-sizing: border-box;
        &:after{
          width: 4px;
          height: 4px;
          border-radius: 100%;
          background-color: #fff;
          content: "";
          position: absolute;
          left: 50%;
          top: 50%;
          transform: translate(-50%,-50%) scale(0);
          transition: transform .15s ease-in;
        }
      }
      .qyh-radio_original{
        opacity: 0;
        outline: none;
        position: absolute;
        z-index: -1;
        top: 0;
        left: 0px;
        right: 0;
        bottom: 0;
        margin: 0;
      }
    }
    .qyh-radio_label{
      font-size: 14px;
      padding-left: 10px;;
    }
  }
  // 选中的样式
  .qyh-radio.is-checked{
    .qyh-radio_input{
      .qyh-radio_inner{
        border-color: #409eff;
        background-color: #409eff;
        &:after{
          transform: translate(-50%,-50%) scale(1);
        }
      }
    }
    .qyh-radio_label{
      color:#409eff;
    }
  }
</style>
