<template>
  <div>
    <slot></slot>
  </div>
</template>
<script lang='ts'>
import { Vue, Prop, Provide,Component } from "vue-property-decorator";
@Component
export default class qyhCheckboxGroup extends Vue {
  name = 'qyhCheckboxGroup'
  @Prop() value?:Number | String;
  @Provide() CheckboxGroup = this;
}
</script>
