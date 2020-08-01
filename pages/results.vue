<template>
  <div class="result">
    <div class="result-back-ground"></div>
    <div class="result-contents">
      <h1>
        <img
          class="result-title-image"
          src="~/assets/images/its-miracle-fusion.png"
          alt="It's Miracle Fusion!"
        >
      </h1>
      <div class="fusion-champion">
        <div class="fusion-champion-item">
          <img :src="results.match.oneNibble.image">
          <span>{{results.match.oneNibble.name}}</span>
        </div>
        <img
          class="cross-mark"
          src="~/assets/images/cross-mark.png"
          alt="×"
        >
        <div class="fusion-champion-item">
          <img :src="results.match.twoNibble.image">
          <span>{{results.match.twoNibble.name}}</span>
        </div>
      </div>
      <div>
        <img
          class="with-image"
          src="~/assets/images/with.png"
          alt="with"
        >
        <img
          class="fusion-champion-alcoholic-beverage"
          :src="results.match.alcoholicBeverage.image"
        >
      </div>
      <button
        class="start-review-button"
        type="button"
      >レビューする</button>
    </div>
    <div class="result-others">
      <h2>その他のマッチする食事</h2>
      <ul class="result-others-list">
        <li
          v-for="nibble in results.candidates"
          :key="nibble.id"
        >
          <img :src="nibble.image">
          <span>{{ nibble.name }}</span>
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
        match: {
          id: 12, // レビューページ用組み合わせID
          alcoholicBeverage: {
            name: "日本酒",
            image: "http://placehold.it/300x500",
          },
          oneNibble: {
            name: "えだまめ",
            image: "http://placehold.it/300x500",
          },
          twoNibble: {
            name: "からあげ",
            image: "http://placehold.it/300x500",
          },
        },
        candidates: [
          {
            name: "からあげ",
            image: "http://placehold.it/300x500",
          },
        ],
      };
    },
  },
};
</script>

<style lang="postcss" scoped>
.result {
  @apply relative w-screen h-screen z-10;
}

.result {
  @apply h-full w-full;
  background: url("~assets/images/result-background.png") no-repeat center;
  background-size: cover;
  position: relative;
  z-index: 0;
}

.result:before {
  content: "";
  background: inherit;
  filter: blur(5px);
  position: absolute;
  top: -5px;
  left: -5px;
  right: -5px;
  bottom: -5px;
  z-index: -1;
}

.result-contents {
  @apply h-full justify-center;
}

.result-title-image {
  @apply block py-8 px-8;
}

.cross-mark {
  width: 32px;
  height: 32px;
}

.fusion-champion {
  @apply flex items-center justify-center mt-4;
}

.fusion-champion-item {
  text-align: center;
}

.fusion-champion-item:first-child,
.fusion-champion-item:last-child {
  @apply mx-4;
}

.fusion-champion-item > span {
  @apply block my-2 font-bold;
}

.fusion-champion-item > img {
  @apply block w-full rounded-md shadow-lg border border-white;
  background-color: white;
  min-height: 200px;
  object-fit: contain;
}

.with-image {
  @apply mx-auto my-6 h-8;
}

.start-review-button {
  @apply block mx-auto mt-8 px-8 py-2 w-1/2 rounded-full text-center border-2 border-white;
  background: linear-gradient(to bottom right, #ff7186, #ff7186 80%, #ff7a5c);
}

.fusion-champion-alcoholic-beverage {
  @apply block mx-auto my-4 rounded-lg shadow-lg;
  max-height: 240px;
}

.result-others {
  @apply bg-gray-700;
}

.result-others > h2 {
  @apply py-4 font-bold text-xl text-center underline;
}

.result-others-list {
  @apply flex flex-wrap justify-center pb-8;
}

.result-others-list > li {
  @apply w-2/5 mx-2 my-1 text-center font-bold relative;
}

.result-others-list img {
  @apply rounded-lg;
}

.result-others-list span {
  @apply absolute text-center inline-block mx-auto font-bold text-xl;
  text-shadow: 1px 2px 3px #787878;
  bottom: 0.5rem;
  left: 1rem;
}
</style>