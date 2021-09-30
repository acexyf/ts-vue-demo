<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3 @click="changeMsg1">{{ msg1 }}</h3>
    <p>
      For a guide and recipes on how to configure / customize this project,<br />
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener"
        >vue-cli documentation</a
      >.
    </p>
  </div>
</template>

<script lang="ts">
import { Component, Prop, PropSync, Vue } from "vue-property-decorator";

@Component
export default class HelloWorld extends Vue {
  @Prop({ type: String, default: "" }) private msg!: string;
  @PropSync("msg1") msg1Sync!: string;
  changeMsg1(): void {
    this.msg1Sync = "new msg";
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
