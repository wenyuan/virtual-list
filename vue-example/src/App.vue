<template>
  <div id="app">
    <button @click="loadData">载入数据</button>
    <button @click="loadDynamicHeightData">载入不定高度的数据</button>
    <!-- <CommonList :listData="listData" :itemSize="100" /> -->
    <!-- <FixedHeightVirtualList :listData="listData" :itemSize="100" /> -->
    <DynamicHeightVirtualList :listData="listData" :estimatedItemSize="100" />
  </div>
</template>

<script>
import { faker } from '@faker-js/faker';
// import CommonList from './components/CommonList.vue'
// import FixedHeightVirtualList from './components/FixedHeightVirtualList.vue'
import DynamicHeightVirtualList from './components/DynamicHeightVirtualList.vue';


export default {
  name: 'App',
  components: {
    // CommonList,
    // FixedHeightVirtualList,
    DynamicHeightVirtualList
  },
  data() {
    return {
      listData: []
    }
  },
  methods: {
    loadData() {
      let now = Date.now();
      let mockData = [];
      for (let i = 0; i < 100000; i++) {
        mockData.push({ id: i, value: `第 ${i + 1} 条数据` });
      }
      this.listData = mockData
      console.log('JS运行时间(ms)：', Date.now() - now);
      setTimeout(() => {
        console.log('总运行时间(ms)：', Date.now() - now);
      }, 0)
    },
    loadDynamicHeightData() {
      let now = Date.now();
      let mockData = [];
      for (let i = 0; i < 100000; i++) {
        mockData.push({ id: i, value: faker.lorem.sentences() });  // 随机长文本
      }
      this.listData = mockData
      console.log('JS运行时间(ms)：', Date.now() - now);
      setTimeout(() => {
        console.log('总运行时间(ms)：', Date.now() - now);
      }, 0)
    }
  }
}
</script>

<style>
html {
  height: 100%;
}

body {
  height: 100%;
  margin: 0;
}

#app {
  height: 100%;
}
</style>
