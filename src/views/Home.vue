<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" @click="clickBtn" />
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
@Component({
  components: {
    HelloWorld,
  },
})
export default class Home extends Vue {
  mounted() {
    console.log(1333311);
    // eslint-disable-next-line
    console.log($("img"));
  }
  clickBtn() {
    console.log("btn");
  }
}
</script>
