<template>
  <div ref="list" class="infinite-list-container">
    <div class="infinite-list-phantom" :style="{ height: listHeight + 'px' }"></div>
    <div class="infinite-list">
      <div ref="items"
        class="infinite-list-item" 
        v-for="item in visibleData" 
        :key="item.id"
        :style="{ height: itemSize + 'px',lineHeight: itemSize + 'px' }"
      >{{ item.value }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonVirtualList',
  props: {
    //所有列表数据
    listData: {
      type:Array,
      default:()=>[]
    },
    //每项高度
    itemSize: {
      type: Number,
      default:200
    }
  },
  computed: {
    //列表总高度
    listHeight() {
      return this.listData.length * this.itemSize;
    },
    //获取真实显示列表数据
    visibleData() {
      return this.listData;
    }
  },
  mounted() {
    this.screenHeight = this.$el.clientHeight;
  }
};
</script>


<style scoped>
.infinite-list-container {
  height: 100%;
  overflow: auto;
  position: relative;
  -webkit-overflow-scrolling: touch;
}

.infinite-list-phantom {
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  z-index: -1;
}

.infinite-list {
  left: 0;
  right: 0;
  top: 0;
  position: absolute;
  text-align: center;
}

.infinite-list-item {
  padding: 10px;
  color: #555;
  box-sizing: border-box;
  border-bottom: 1px solid #999;
}
</style>
