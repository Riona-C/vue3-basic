<template>
  <div id="app">
    <div class="num">
      {{ count }}
      {{ double }}
    </div>
    <button class="add" @click="add">add</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed, reactive, toRefs } from 'vue';
interface DataProps {
  count: number;
  add: () => void;
  double: number;
}

export default defineComponent({
  setup() {
    // ref 定义数据   ---   返回
    // const count = ref(0); // ref对象可以直接取count中的value值
    // // 计算属性，是一个函数，传入一个回调函数参数   ----  返回
    // const double = computed(() => {
    //   return count.value * 2
    // })
    // // methods 直接定义箭头函数  ---  返回
    // const add = () => {
    //   count.value++;
    // }
    const data: DataProps = reactive({
      count: 0,
      add: () => { data.count++ },
      double: computed(() => data.count * 2)
    })

    const refData = toRefs(data);
    return {
      ...refData
    }
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
