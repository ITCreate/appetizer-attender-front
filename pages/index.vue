<template>
  <div class="container">
    <div>
      <img src="~assets/image/main-logo-white.png" />
      <h1>今日のあなたはどのお酒？</h1>
      <ul v-for="alchole in alcoholicBeverages" :key="alchole.id">
        <li>
          <img :src="alchole.image" @click="redirectSwipe(alchole)" width="100" height="100" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      alcoholicBeverages: [],
    }
  },
  created() {
    this.alcoholicBeverages = this.fetchAlcoholicBeverages();
  },
  methods: {
    fetchAlcoholicBeverages() {
      // APIを叩く
      // バックエンドは実装中のためとりあえずダミーデータ
      return [
        {
          id: 1,
          name: "白ワイン",
          image: require("~/assets/image/white_wine.png"),
        },
        {
          id: 2,
          name: "ビール",
          image: require("~/assets/image/drink_beer.png"),
        },
        {
          id: 3,
          name: "日本酒",
          image: require("~/assets/image/drink_nihonsyu.png"),
        },
        {
          id: 4,
          name: "カクテル",
          image: require("~/assets/image/drink_cocktail.png"),
        },
        {
          id: 5,
          name: "赤ワイン",
          image: require("~/assets/image/red_wine.png"),
        },
        {
          id: 6,
          name: "ハイボール",
          image: require("~/assets/image/party_highball_glass.png"),
        }
      ];
    },
    redirectSwipe(alchole) {
      // 遷移先にalchole情報も渡す
      this.$router.push("/swipe");
    },
  }
}
</script>

<style>
</style>
