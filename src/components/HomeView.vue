<template>
  <div>
    <TopView> </TopView>
    <div id="home">
      <div class="tabs">
        <el-tabs v-model="activeName" type="card" @tab-click="handleClick">
          <el-tab-pane label="头条" name="news">头条</el-tab-pane>
          <el-tab-pane label="体育" name="sport">体育</el-tab-pane>
          <el-tab-pane label="健康" name="health">健康</el-tab-pane>
          <el-tab-pane label="娱乐" name="fun">娱乐</el-tab-pane>
        </el-tabs>
      </div>

      <div class="block">
        <!-- <span class="demonstration">默认 Hover 指示器触发</span> -->
        <el-carousel class="carousel">
          <el-carousel-item v-for="item in images" :key="item">
            <img :src="item" />
          </el-carousel-item>
        </el-carousel>
      </div>
    </div>
  </div>
</template>

<script>
import TopView from "./TopNavView.vue";

export default {
  name: "HomeVue",
  props: {
    msg: String
  },
  components: {
    TopView
  },
  data() {
    return {
      images: [
        "https://www.guet.edu.cn/__local/C/10/31/B8A46818B0B172E9F140DDF04AE_EF2B4179_37ACE.jpg",
        "https://www.guet.edu.cn/__local/1/B2/E6/9B3C02F46CA0AA89F2E7AA21469_785F1617_CC0A.jpg"
      ],
      activeName: "second"
    };
  },
  created() {
    this.$axios.get("/categories").then(response => {
      console.log(response.data);
    });
  },
  methods: {
    handleClick(tab, event) {
      console.log(tab, event);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.carousel {
  height: 410px;
  width: 1280px;
  margin: auto;
  margin-top: 10px;
}
.tabs {
  margin: auto;
}
</style>
