<template>
  <div class="home">
    <img alt="Vue logo"
         src="../assets/logo.png">
    <HelloWorld msg="vue3.0 测试模块 " />
  </div>
  <div>
    <button v-for="(item,index) in nameArray"
            v-bind:key="index"
            @click="selectHroFun(index)">{{item}}</button>
  </div>
  <div>
    <P>{{selectHero}}</P>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src

export default defineComponent({
  name: "Home",
  setup() {
    const nameArray = ref(["飞人", "蝙蝠侠", "蜘蛛侠"]);
    const selectHero = ref("");
    const selectHroFun = (inde: number) => {
      selectHero.value = nameArray.value[inde];
      console.log(selectHero);
    };

    return {
      nameArray,
      selectHroFun,
      selectHero,
    };
  },
  components: {
    HelloWorld,
  },
});
</script>
