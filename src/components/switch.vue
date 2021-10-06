<template>
  <div class="qyh-switch" :class="{ 'is-checked': value }" @click="handleClick">
    <span class="qyh-switch_core" ref="core">
      <span class="qyh-switch_button"></span>
    </span>
    <input type="checkbox" class="qyh-switch_input" ref="input" />
  </div>
</template>
<script lang='ts'>
import { Component, Vue, Prop, Watch } from "vue-property-decorator";

@Component({})
export default class qyhRadio extends Vue {
  name = "qyhSwitch";
  @Prop() value: any;
  @Prop() activeColor: any;
  @Prop() inactiveColor: any;
  mounted() {
    // 修改开关颜色
    if (this.activeColor || this.inactiveColor) {
      const color = !this.value ? this.activeColor : this.inactiveColor;
      (this.$refs as any).core.style.borderColor = color;
      (this.$refs as any).core.style.backgroundColor = color;
    }
    // 控制checkbox的值,input值同步value值
    (this.$refs as any).input.checked = this.value;
  }
  @Watch("value")
  changeColor(e: any) {
    if (this.activeColor || this.inactiveColor) {
      var color = !e ? this.activeColor : this.inactiveColor;
      (this.$refs as any).core.style.borderColor = color;
      (this.$refs as any).core.style.backgroundColor = color;
    }
  }
  handleClick() {
    this.$emit("input", !this.value);
    // 控制checkbox的值,input值同步value值
    (this.$refs as any).input.checked = this.value;
  }
}
</script>
<style lang="scss" scoped>
.qyh-switch {
  display: inline-block;
  align-items: center;
  position: relative;
  font-size: 14px;
  line-height: 20px;
  vertical-align: middle;
  .qyh-switch_core {
    margin: 0;
    display: inline-block;
    position: relative;
    width: 40px;
    height: 20px;
    border: 1px solid #dcdfe6;
    outline: none;
    border-radius: 10px;
    box-sizing: border-box;
    background: #dcdfe6;
    cursor: pointer;
    transition: border-color 0.3s, background-color 0.3s;
    vertical-align: middle;
    .qyh-switch_button {
      position: absolute;
      top: 1px;
      left: 1px;
      border-radius: 100%;
      transition: all 0.3s;
      width: 16px;
      height: 16px;
      background-color: #fff;
    }
  }
}
// 选中样式
.is-checked {
  .qyh-switch_core {
    border-color: #409eff;
    background-color: #409eff;
    .qyh-switch_button {
      transform: translateX(20px);
    }
  }
}
// 隐藏input标签
.qyh-switch_input {
  position: absolute;
  width: 0;
  height: 0;
  opacity: 0;
  margin: 0;
}
</style>
