<template >
  <button
    class="qyh-button"
    :class="[`qyh-button-${size}`, `qyh-button-${type}`]"
    :style="{ width: Width,height: Height }"
  >
    <slot>按钮</slot>
  </button>
</template>
<script lang='ts'>
import { Component, Vue, Prop, Watch } from "vue-property-decorator";

@Component({})
export default class Button extends Vue {
  @Prop({
    type: String,
    required: false,
    default: "small",
  })
  size?: string;
  @Prop({
    type: String,
    required: false,
    default: "primary",
  })
  type: string;
  @Prop({
    type: Number || String,
    required: false,
    default: "40px",
  })
  width: Number | String;
  @Prop({
    type: Number || String,
    required: false,
    default: "20px",
  })
  height?: Number | String;

  get Width() {
    if (typeof this.width === "number") {
      return this.width + "px";
    } else {
      return this.width;
    }
  }
  get Height() {
    if (typeof this.height === "number") {
      return this.height + "px";
    } else {
      return this.height;
    }
  }
}
</script>
<style lang="scss" scoped>
.qyh-button {
  display: inline-block;
  line-height: 1;
  white-space: nowrap;
  cursor: pointer;
  background: #ffffff;
  border: 1px solid #dcdfe6;
  color: #606266;
  -webkit-appearance: none;
  text-align: center;
  box-sizing: border-box;
  outline: none;
  margin: 0;
  transition: 0.1s;
  font-weight: 500;
  //禁止元素的文字被选中
  -moz-user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  font-size: 14px;
  border-radius: 4px;
  &:hover,
  &:focus {
    color: #409eff;
    border-color: #c6e2ff;
    background-color: #ecf5ff;
  }
}
.qyh-button-small {
  width: 40px;
  height: 20px;
}
.qyh-button-mini {
  width: 20px;
  height: 10px;
}
.qyh-button-medium {
  width: 60px;
  height: 30px;
}
.qyh-button-primary {
  color: #fff;
  background-color: #409eff;
  border-color: #409eff;
  &:hover,
  &:focus {
    background: #66b1ff;
    background-color: #66b1ff;
    color: #fff;
  }
}
.qyh-button-success {
  color: #fff;
  background-color: #67c23a;
  border-color: #67c23a;
  &:hover,
  &:focus {
    background: #85ce61;
    background-color: #85ce61;
    color: #fff;
  }
}
.qyh-button-info {
  color: #fff;
  background-color: #909399;
  border-color: #909399;
  &:hover,
  &:focus {
    background: #a6a9ad;
    background-color: #a6a9ad;
    color: #fff;
  }
}
.qyh-button-warning {
  color: #fff;
  background-color: #e6a23c;
  border-color: #e6a23c;
  &:hover,
  &:focus {
    background: #ebb563;
    background-color: #ebb563;
    color: #fff;
  }
}
.qyh-button-danger {
  color: #fff;
  background-color: #f56c6c;
  border-color: #f56c6c;
  &:hover,
  &:focus {
    background: #f78989;
    background-color: #f78989;
    color: #fff;
  }
}
// 朴素按钮样式
.qyh-button.is-plain {
  &:hover,
  &:focus {
    background: #fff;
    border-color: #489eff;
    color: #409eff;
  }
}
.qyh-button-primary.is-plain {
  color: #409eff;
  background: #ecf5ff;
  &:hover,
  &:focus {
    background: #409eff;
    border-color: #409eff;
    color: #fff;
  }
}
.qyh-button-success.is-plain {
  color: #67c23a;
  background: #c2e7b0;
  &:hover,
  &:focus {
    background: #67c23a;
    border-color: #67c23a;
    color: #fff;
  }
}
.qyh-button-info.is-plain {
  color: #909399;
  background: #d3d4d6;
  &:hover,
  &:focus {
    background: #909399;
    border-color: #909399;
    color: #fff;
  }
}
.qyh-button-warning.is-plain {
  color: #e6a23c;
  background: #f5dab1;
  &:hover,
  &:focus {
    background: #e6a23c;
    border-color: #e6a23c;
    color: #fff;
  }
}
.qyh-button-danger.is-plain {
  color: #f56c6c;
  background: #fbc4c4;
  &:hover,
  &:focus {
    background: #f56c6c;
    border-color: #f56c6c;
    color: #fff;
  }
}
// round属性
.qyh-button.is-round {
  border-radius: 20px;
  padding: 12px 23px;
}
// circle属性
.qyh-button.is-circle {
  border-radius: 50%;
  padding: 12px;
}
// icon配套样式
.qyh-button [class*="one-icon-"] + span {
  margin-left: 5px;
}
// disabled属性
.qyh-button.is-disabled {
  cursor: no-drop;
}
</style>
