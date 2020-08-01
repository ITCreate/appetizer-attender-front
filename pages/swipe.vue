<template>
  <div id="swipe">
    <div class="swipe-header">
      <img
        src="~/assets/images/logo.png"
        alt=""
      >
    </div>
    <div class="swipe-main">
      <VueTinder
        ref="tinder"
        key-name="id"
        :queue.sync="queue"
        :offset-y="10"
        @submit="onSubmit"
      >
        <template slot-scope="scope">
          <div
            class="pic"
            :style="{'background-image': `url(${scope.data.image})`}"
          />
        </template>
        <img
          class="like-pointer"
          slot="like"
          src="~/assets/images/like-txt.png"
        >
        <img
          class="nope-pointer"
          slot="nope"
          src="~/assets/images/nope-txt.png"
        >
        <img
          class="super-pointer"
          slot="super"
          src="~/assets/images/super-txt.png"
        >
      </VueTinder>
      <div class="swipe-buttons">
        <div class="swipe-button">
          <img
            src="~/assets/images/nope.png"
            @click="decide('nope'); cantEat();"
          >
          <span>食べれない</span>
        </div>
        <div class="swipe-button">
          <img
            src="~/assets/images/super-like.png"
            @click="decide('super'); canEat();"
          >
          <span>好きなもの</span>
        </div>
        <div class="swipe-button">
          <img
            src="~/assets/images/like.png"
            @click="decide('like'); canEat();"
          >
          <span>食べれる</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VueTinder from "vue-tinder";

export default {
  components: {
    VueTinder,
  },
  data: () => ({
    alcoholicBeverage: {},
    nibbles: [],
    queue: [],
    offset: 0,
  }),
  created() {
    this.getAlcoholicBeverage();
    this.fetchNibbles();
  },
  methods: {
    getAlcoholicBeverage() {
      this.alcoholicBeverage = this.$route.params.alcoholicBeverage;
    },
    async fetchNibbles() {
      await this.$axios.get("/nibbles").then(res => {
        this.nibbles = res.data;
        this.mock();
      });
    },
    mock() {
      const list = [];
      const nibbles = this.nibbles;
      for (let i = 0; i < nibbles.length + 1; i++) {
        list.push({
          id:
            typeof nibbles[this.offset] === "undefined"
              ? undefined
              : nibbles[this.offset].id,
          name:
            typeof nibbles[this.offset] === "undefined"
              ? undefined
              : nibbles[this.offset].name,
          image:
            typeof nibbles[this.offset] === "undefined"
              ? undefined
              : nibbles[this.offset].image,
        });
        this.offset++;
      }
      this.queue = this.queue.concat(list);
    },
    onSubmit({ item }) {
      this.saveSwipe(item, "食べれるか食べられへんかみたいなステータス取って渡したいけどやり方が分からん");
      if (this.canMoveResult()) {
        // スワイプ情報も遷移先に渡すようにする
        this.$router.push({ name: "results", params: {
          swipes: "スワイプ情報がここに入ります"
        } });
      }
      if (this.queue.length < 3) {
        this.mock();
      }
    },
    decide(choice) {
      this.$refs.tinder.decide(choice);
    },
    canEat() {
      this.saveSwipe(item, "食べれるか食べられへんかみたいなステータス取って渡したいけどやり方が分からん");
    },
    cantEat() {
      this.saveSwipe(item, "食べれるか食べられへんかみたいなステータス取って渡したいけどやり方が分からん");
    },
    saveSwipe(item, status) {
      // ゴニョる
    },
    canMoveResult() {
      return this.queue
        .map((v) => v.name)
        .every((v) => typeof v === "undefined");
    },
  },
};
</script>

<style lang="postcss">
.swipe-header {
  padding-top: 16px;
  height: 48px;
  display: flex;
  justify-content: center;
}

.swipe-header > img {
  display: block;
  height: 32px;
}

.swipe-main {
  height: calc(100% - 64px);
  margin: 1rem auto;
}

#swipe {
  @apply h-screen;
}

#swipe .vue-tinder {
  margin: auto;
  width: calc(100%);
  height: calc(80%);
  min-width: 300px;
  max-width: 300px;
}

.nope-pointer,
.like-pointer {
  position: absolute;
  z-index: 1;
  top: 20px;
  width: 140px;
  height: 96px;
  object-fit: contain;
}

.nope-pointer {
  right: 10px;
}

.like-pointer {
  left: 10px;
}

.super-pointer {
  position: absolute;
  z-index: 1;
  bottom: 80px;
  left: 0;
  right: 0;
  margin: auto;
  width: 200px;
  height: 144px;
  object-fit: contain;
}

.pic {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
}

.swipe-buttons {
  margin: 48px auto 0;
  height: 65px;
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 300px;
  max-width: 355px;
}

.swipe-button {
  width: 33%;
  text-align: center;
  font-weight: bold;
  color: #575757;
}

.swipe-button > span {
  display: block;
  margin-top: 5px;
}

.swipe-buttons img {
  margin: 0 auto;
  box-shadow: 0 4px 9px rgba(0, 0, 0, 0.15);
  border-radius: 50%;
  cursor: pointer;
  -webkit-tap-highlight-color: transparent;
}

.swipe-buttons img:nth-child(2n + 1) {
  width: 53px;
}

.swipe-buttons img:nth-child(2n) {
  width: 65px;
}

.swipe-buttons img:nth-last-child(1) {
  margin-right: 0;
}
</style>