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
            :style="{'background-image': `url(${scope.data.id})`}"
          />
        </template>
        <img
          class="like-pointer"
          slot="like"
          src="~/assets/like-txt.png"
        >
        <img
          class="nope-pointer"
          slot="nope"
          src="~/assets/nope-txt.png"
        >
        <img
          class="super-pointer"
          slot="super"
          src="~/assets/super-txt.png"
        >
      </VueTinder>
      <div class="swipe-buttons">
        <div class="swipe-button">
          <img
            src="~/assets/images/nope.png"
            @click="decide('nope')"
          >
          <span>合わない</span>
        </div>
        <div class="swipe-button">
          <img
            src="~/assets/images/super-like.png"
            @click="decide('super')"
          >
          <span>めっちゃ合う</span>
        </div>
        <div class="swipe-button">
          <img
            src="~/assets/images/like.png"
            @click="decide('like')"
          >
          <span>合う</span>
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
    queue: [],
    offset: 0,
  }),
  created() {
    this.mock();
  },
  methods: {
    mock() {
      const list = [];
      // APIを叩く
      // 現在バックエンドは実装中なのでダミーデータ
      const nibbles = this.fetchNibbles();
      for (let i = 0; i < nibbles.length + 1; i++) {
        list.push({
          id:
            typeof nibbles[this.offset] === "undefined"
              ? undefined
              : nibbles[this.offset].image,
          name:
            typeof nibbles[this.offset] === "undefined"
              ? undefined
              : nibbles[this.offset].name,
        });
        this.offset++;
      }
      this.queue = this.queue.concat(list);
    },
    onSubmit({ item }) {
      // ここにスワイプ情報を保存する処理を書く
      if (this.canMoveResult()) {
        // スワイプ情報も遷移先に渡すようにする
        this.$router.push("/result");
      }
      if (this.queue.length < 3) {
        this.mock();
      }
    },
    decide(choice) {
      this.$refs.tinder.decide(choice);
    },
    fetchNibbles() {
      return [
        {
          name: "枝豆",
          image:
            "https://cn.bing.com//th?id=OHR.AdelieBreeding_ZH-CN1750945258_UHD.jpg&pid=hp&w=720&h=1280&rs=1&c=4&r=0",
        },
        {
          name: "チーズ",
          image:
            "https://cn.bing.com//th?id=OHR.BarcolanaTrieste_ZH-CN5745744257_UHD.jpg&pid=hp&w=720&h=1280&rs=1&c=4&r=0",
        },
        {
          name: "ポテチ",
          image:
            "https://cn.bing.com//th?id=OHR.RedRocksArches_ZH-CN5664546697_UHD.jpg&pid=hp&w=720&h=1280&rs=1&c=4&r=0",
        },
        {
          name: "餃子",
          image:
            "https://cn.bing.com//th?id=OHR.LofotenSurfing_ZH-CN5901239545_UHD.jpg&pid=hp&w=720&h=1280&rs=1&c=4&r=0",
        },
      ];
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
  width: 64px;
  height: 64px;
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
  width: 112px;
  height: 78px;
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