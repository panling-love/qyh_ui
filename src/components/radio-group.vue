<template>
  <div class="one-radio-group">
    <slot></slot>
  </div>
</template>
<script lang='ts'>
import { Vue, Prop, Provide,Component } from "vue-property-decorator";
import qyhRadio from "./radio.vue"
@Component({
  components: {
    qyhRadio,
  },
})
export default class qyhRadioGroup extends Vue {
  name = 'qyhRadioGroup'
  
  @Prop() value?:Number | String;
  @Provide() RadioGroup = this;
}
</script>
