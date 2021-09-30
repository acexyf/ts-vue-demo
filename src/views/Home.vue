<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" @click="clickBtn" />
    <div>{{ fullName | filterName }}</div>
    <HelloWorld
      msg="sssWelcome to Your Vue.js + TypeScript App"
      :msg1.sync="firtName"
    />
    <MyInput v-model="namess" />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
import MyInput from "@/components/MyInput.vue";
Component.registerHooks(["beforeRouteLeave", "beforeRouteEnter"]);

@Component({
  components: {
    HelloWorld,
    MyInput,
  },
  filters: {
    filterName(val: string) {
      return val + "：filter name";
    },
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

  beforeRouteEnter(to: any, from: any, next: any) {
    console.log("beforeRouteLeave");
    next();
  }
  private firtName = "tom";
  private lastName = "bluce";
  private namess = "";

  get fullName(): string {
    console.log("getter");

    return `${this.firtName} ${this.lastName}`;
  }

  @Watch("firtName")
  changeFirstName(val: string, oldVal: string) {
    console.log(val);
  }
}
</script>
