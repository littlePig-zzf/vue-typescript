<template>
  <div class="hello">
    <h2>{{ msg }}</h2>
    <!-- <Button type="primary" @click="btnClick">Primary</Button> -->
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  btnClick() {
    this.$emit("btnHandle", "s");
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
