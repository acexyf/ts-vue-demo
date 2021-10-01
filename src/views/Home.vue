<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" @click="clickBtn" />
    <div ref="refDiv">{{ fullName | filterName }}</div>
    <HelloWorld
      msg="sssWelcome to Your Vue.js + TypeScript App"
      :msg1.sync="firtName"
    />
    <div>namess:{{ namess }}</div>
    <MyInput v-model="namess" @click-btn="emitFn" ref="inputRef" />
    <div @click="clickSubmit">submit</div>
  </div>
</template>

<script lang="ts">
import { Component, Ref, Vue, Watch } from "vue-property-decorator";
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
  @Ref() readonly refDiv!: HTMLElement;
  @Ref("refDiv") readonly newRef!: HTMLElement;
  @Ref() readonly inputRef!: MyInput;
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
  private namess = "eee";

  get fullName(): string {
    console.log("getter");

    return `${this.firtName} ${this.lastName}`;
  }

  @Watch("firtName")
  changeFirstName(val: string, oldVal: string) {
    console.log(val);
  }

  emitFn(item: any, index: number): void {
    console.log("parent emit", item, index);
  }

  clickSubmit(): void {
    console.log(this.refDiv);
    console.log(this.newRef);
    
  }
}
</script>
