<template lang="">
  <div>
    <input class='qyh-input' :type='type' :value='value' @input='inputHandle'
    :max='max'
    :min='min'
    :maxlength='maxlength'
    :placeholder='placeholder'
    ref="qyh-input"
    ><span class='icon-input-clearable' @click='clearable'>x</span>
   </input>
  </div>
</template>
<script lang='ts'>
import { Component, Vue, Prop,Watch } from "vue-property-decorator";

@Component({})
export default class Input extends Vue {
  @Prop() type?: string;
  @Prop() value?: Number|String;
  @Prop() max?: Date|Number;
  @Prop() maxlength?: Number;
  @Prop() minlength?: Number;
  @Prop() min?: Date|Number;
  @Prop({
    default: 'please input'
  }) placeholder?: Date|Number;
  inputHandle(e:any) {
    if(this.minlength) {
      if(e.target.value.length < this.minlength) {
        e.target.value = this.value
      } else {
        this.$emit('input', e.target.value)
      }
    } else {
      this.$emit('input', e.target.value)
    }
  }
  clearable() {
    this.$emit('input', '');
  }
}
</script>
<style lang="scss" scoped>
  .qyh-input{
    position: relative;
    font-size: 14px;
    display: inline-block;
    .qyh-input_inner{
      -webkit-appearance: none;
      background-color: #fff;
      background-image: none;
      border: 1px solid #dcdfe6;
      border-radius: 4px;
      box-sizing: border-box;
      color: #606266;
      display: inline-block;
      font-size: inherit;
      height: 40px;
      line-height: 40px;
      outline: none;
      padding: 0 15px;
      transition: border-color .2s cubic-bezier(.645,045,.355,1);
      width: 100%;

      &:focus{
        outline: none;
        border-color: #409eff;
      }
      // input禁用样式
      &.is-disabled{
        background-color: #f5f7fa;
        border-color: #e4e7ed;
        color: #c0c4cc;
        cursor:not-allowed;
      }
    }
  }
  // 后面加suffix的意思是后面如果有后缀的话，触发该样式
  .qyh-input_suffix{
    .qyh-input_inner{
      padding-right: 30px;
    }
    .qyh-input_suffix{
      position: absolute;
      right: 10px;
      height: 100%;
      top: 0;
      line-height: 40px;
      text-align: center;
      color: #c0c4cc;
      transition: all .3s;
      z-index: 900;
      i{
        color: #c0c4cc;
        font-size: 14px;
        cursor: pointer;
        transition: color .2s cubic-bezier(.645,.045,.355,1);
      }
    }
  }
  .icon-input-clearable {
    position: absolute;
    display: inline-block;
    width: 22px;
    height: 22px;
    background-color: rgba(255, 255, 255, .5);
    cursor: pointer;
  }
</style>
