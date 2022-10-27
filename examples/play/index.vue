<template>
  <div style="margin: 20px">
    <!-- <el-input v-model="input" placeholder="请输入内容"></el-input> -->
    <!-- <el-cascader
      :props="props"
      class="map_select"
      filterable
      @change="handleChange"
    ></el-cascader> -->
    <template>
      <el-carousel indicator-position="none" :interval="10000">
        <el-carousel-item v-for="item in 5" :key="item">
          <h3>{{ item }}</h3>
        </el-carousel-item>
      </el-carousel>
    </template>
  </div>
</template>

<style>
.el-carousel__item h3 {
  text-align: center;
  color: #475669;
  font-size: 18px;
  opacity: 0.75;
  line-height: 300px;
  margin: 0;
}

.el-carousel__item:nth-child(2n) {
  background-color: #99a9bf;
}

.el-carousel__item:nth-child(2n + 1) {
  background-color: #d3dce6;
}
</style>

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
