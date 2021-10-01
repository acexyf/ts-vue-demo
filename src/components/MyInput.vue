<template>
  <div>
    <div>v-model: {{ val }}</div>
    <div @click="clickBtn">myinput</div>
    <input type="text" :value="val" @input="changeInput" />
  </div>
</template>

<script lang="ts">
import { Component, Emit, Model, Vue } from "vue-property-decorator";

@Component
export default class MyInput extends Vue {
  private item = { id: 3 };

  @Model("input", { type: String }) readonly val!: string;

  @Emit("input")
  clickBtn() {
    return "new eeee";
  }

  @Emit("input")
  changeInput(ev: any) {
    return ev.target.value;
  }
}
</script>

<style></style>
