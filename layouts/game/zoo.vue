<template>
  <v-app
    :style="{minWidth: device ? 900 + 'px' : 'auto'}"
  >
    <nuxt
      v-if="device"
    />
    <div
      v-else-if="!device"
      class="center text-center"
    >
      <p>请使用电脑访问：{{ url }}</p>
      <p>希望你玩的开心啊～</p>
      <p>内啥，理性游戏，注意情绪...</p>
      <nuxt-link to="/game">返回游戏合集</nuxt-link>
    </div>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      device: "",
      url: ""
    };
  },
  mounted() {
    const userAgent = navigator.userAgent;
    this.device = !userAgent.includes("iPhone") && !userAgent.includes("Android");

    let url = location.href;
    if (url.charAt(url.length - 1) === "/")
      url = url.substring(0, url.length - 1);
    this.url = url;
  },
  head: {
    titleTemplate: "%s • DexterYu 的游戏",
    meta: [
      { hid: "description", name: "description", content: "前端团队智勇大闯关" },
      { name: "keywords", content: "前端游戏" }
    ]
  }
};
</script>

<style scoped>
/deep/ .text-center {
  font-size: 20px;
  letter-spacing: 2px;
}
</style>
