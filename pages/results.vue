<template>
  <div>
    <div>
      <h1>It's Miracle Fusion!</h1>
      <div>
        <img :src="results.top_two[0].image">
        <p>×</p>
        <img :src="results.top_two[1].image">
      </div>
      <div>
        <p>with</p>
        <img :src="results.candidates[2].image">
      </div>
      <button type="button">レビューする</button>
    </div>
    <div>
      <h2>その他のマッチリスト</h2>
      <ul v-for="nibble in results.candidates" :key="nibble.id">
        <li>
          <img :src="nibble.image">
          <p>{{ nibble.name }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    results: [],
  }),
  created() {
    this.results = this.fetchResults();
  },
  methods: {
    fetchResults() {
      // 結果を取得するAPIを叩く
      // バックエンド対応待ち
      // とりあえずダミーデータ
      return {
        top_two: [
          { id: 1, name: "餃子", image: "https://1.bp.blogspot.com/-JgCCcKaPehk/XuRAqUWJgLI/AAAAAAABZgQ/hY77s2QpJjQG1kk78jR91O4LRrinBRWaQCNcBGAsYHQ/s1600/food_jelly_fry.png" },
          { id: 2, name: "ごはん", image: "https://4.bp.blogspot.com/-S9iMvM5-DcI/VoX5L4XQDlI/AAAAAAAA2TA/JiN-OviBAcE/s800/food_mamegohan.png" },
        ],
        candidates: [
          { id: 1, name: "パスタ", image: "https://1.bp.blogspot.com/-s0F8ah-KmmA/XobTIIgFn3I/AAAAAAABYFA/RLUBWSpeAusE4R2SmGPqaa0ZLeb05MybQCNcBGAsYHQ/s1600/food_gyouza_age.png" },
          { id: 2, name: "パスタ", image: "https://1.bp.blogspot.com/-s0F8ah-KmmA/XobTIIgFn3I/AAAAAAABYFA/RLUBWSpeAusE4R2SmGPqaa0ZLeb05MybQCNcBGAsYHQ/s1600/food_gyouza_age.png" },
          { id: 3, name: "パスタ", image: "https://1.bp.blogspot.com/-s0F8ah-KmmA/XobTIIgFn3I/AAAAAAABYFA/RLUBWSpeAusE4R2SmGPqaa0ZLeb05MybQCNcBGAsYHQ/s1600/food_gyouza_age.png" },
          { id: 4, name: "パスタ", image: "https://1.bp.blogspot.com/-s0F8ah-KmmA/XobTIIgFn3I/AAAAAAABYFA/RLUBWSpeAusE4R2SmGPqaa0ZLeb05MybQCNcBGAsYHQ/s1600/food_gyouza_age.png" },
          { id: 5, name: "パスタ", image: "https://1.bp.blogspot.com/-s0F8ah-KmmA/XobTIIgFn3I/AAAAAAABYFA/RLUBWSpeAusE4R2SmGPqaa0ZLeb05MybQCNcBGAsYHQ/s1600/food_gyouza_age.png" },
          { id: 6, name: "パスタ", image: "https://1.bp.blogspot.com/-s0F8ah-KmmA/XobTIIgFn3I/AAAAAAABYFA/RLUBWSpeAusE4R2SmGPqaa0ZLeb05MybQCNcBGAsYHQ/s1600/food_gyouza_age.png" },
        ],
      };
    }
  }
};
</script>

<style>
</style>