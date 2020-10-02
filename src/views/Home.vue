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
import { reactive, toRefs } from "vue";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src

interface DataProps {
  nameArray: string[];
  selectHero: string;
  selectHroFun: (index: number) => void;
}

export default {
  name: "Home",
  setup() {
    const data: DataProps = reactive({
      nameArray: ["飞人", "蝙蝠侠", "蜘蛛侠"],
      selectHero: "",
      selectHroFun: (inde: number) => {
        data.selectHero = data.nameArray[inde];
      },
    });

    const refsData = toRefs(data);

    return {
      ...refsData,
    };
  },

  components: {
    HelloWorld,
  },
};
</script>
