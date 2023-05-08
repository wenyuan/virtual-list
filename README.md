# Virtual List
高性能渲染大量数据（虚拟列表）实验用例。

## 项目结构

```
virtual-list/
├── 10w-data-render.html  # 测试大量数据直接渲染的效果
├── vue-example/          # 基于Vue.js写的测试用例
│   │── src/
│   │  │── App.vue        # 父组件（调用方），在这里选择用哪个列表组件来渲染数据
│   │  │── components/    # 封装的列表组件 
│   │  │   │── CommonList.vue  # 直接渲染
│   │  │   └── FixedHeightVirtualList.vue  # 固定高度虚拟列表
│   │  └── ...
│   └── ...
└── ...
```
