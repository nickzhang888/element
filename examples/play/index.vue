<template>
  <div style="margin: 20px">
    <!-- <el-input v-model="input" placeholder="请输入内容"></el-input> -->
    <el-cascader
      :props="props"
      class="map_select"
      filterable
      @change="handleChange"
    ></el-cascader>
  </div>
</template>

<script>
 let id = 0;
export default {
  data() {
    return {
      input: "Hello Element UI!",
      props: {
        lazy: true,
        lazyLoad: this.lazyLoad,
      },
    };
  },
  methods: {
    handleChange(value) {},
    lazyLoad(node, resolve) {
      const { level } = node;
      setTimeout(() => {
        const nodes = Array.from({ length: level + 1 }).map((item) => ({
          value: ++id,
          label: `选项${id}`,
          leaf: level >= 2,
        }));
        // 通过调用resolve将子节点数据返回，通知组件数据加载完成
        resolve(nodes);
      }, 1000);
    },
  },
};
</script>
