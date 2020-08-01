<template>
  <div class="container mx-auto">
    <div class="text-center">
      <div class="result mt-4">
        <h1 class="title">RESULT!</h1>
        <p>このツマミが</p>
        <p>お酒に合う！</p>
        <img :src="results[0].image" class="image">
        <strong>×</strong>
        <img :src="results[1].image" class="image">
        <br>
        <strong>♡</strong>
        <br>
        <img :src="results[2].image" class="image">
      </div>
      <div class="candidate mb-4">
        <h2 class="title">その他の候補</h2>
        <img src="~/assets/images/sample4.jpg" class="image">
        <strong>×</strong>
        <img src="~/assets/images/sample5.jpg" class="image">
        <br>
        <img src="~/assets/images/sample6.jpg" class="image">
        <strong>×</strong>
        <img src="~/assets/images/sample7.jpg" class="image">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    result: [],
  }),
  created() {
    this.fetchResult();
  },
  methods: {
    fetchResult() {
      // 結果を取得するAPIを叩く
      // バックエンド対応待ち
      // とりあえずダミーデータ
      this.results = [
        { id: 1, name: "餃子", image: "https://1.bp.blogspot.com/-JgCCcKaPehk/XuRAqUWJgLI/AAAAAAABZgQ/hY77s2QpJjQG1kk78jR91O4LRrinBRWaQCNcBGAsYHQ/s1600/food_jelly_fry.png" },
        { id: 1, name: "ごはん", image: "https://4.bp.blogspot.com/-S9iMvM5-DcI/VoX5L4XQDlI/AAAAAAAA2TA/JiN-OviBAcE/s800/food_mamegohan.png" },
        { id: 1, name: "パスタ", image: "https://1.bp.blogspot.com/-s0F8ah-KmmA/XobTIIgFn3I/AAAAAAABYFA/RLUBWSpeAusE4R2SmGPqaa0ZLeb05MybQCNcBGAsYHQ/s1600/food_gyouza_age.png" },
      ];
    }
  }
};
</script>

<style>
.title {
  font-size: 30px;
}
.image {
  width: 20%;
  display: inline-block;
}
</style>