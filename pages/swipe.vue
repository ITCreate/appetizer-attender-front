<template>
  <div id="app">
    <VueTinder ref="tinder" key-name="id" :queue.sync="queue" :offset-y="10" @submit="onSubmit">
      <template slot-scope="scope">
        <div class="pic" :style="{'background-image': `url(${scope.data.id})`}"/>
      </template>
      <img class="like-pointer" slot="like" src="~/assets/like-txt.png">
      <img class="nope-pointer" slot="nope" src="~/assets/nope-txt.png">
      <img class="super-pointer" slot="super" src="~/assets/super-txt.png">
    </VueTinder>
    <div class="btns">
      <img src="~/assets/nope.png" @click="decide('nope')">
      <img src="~/assets/super-like.png" @click="decide('super')">
      <img src="~/assets/like.png" @click="decide('like')">
    </div>
  </div>
</template>

<script>
import VueTinder from 'vue-tinder'

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
        list.push({ id: nibbles[this.offset] });
        this.offset++;
      }
      this.queue = this.queue.concat(list);
    },
    onSubmit({ item }) {
      if (this.queue.length < 3) {
        this.mock();
      }
    },
    decide(choice) {
      this.$refs.tinder.decide(choice);
    },
    fetchNibbles() {
      return [
        "https://cn.bing.com//th?id=OHR.AdelieBreeding_ZH-CN1750945258_UHD.jpg&pid=hp&w=720&h=1280&rs=1&c=4&r=0",
        "https://cn.bing.com//th?id=OHR.BarcolanaTrieste_ZH-CN5745744257_UHD.jpg&pid=hp&w=720&h=1280&rs=1&c=4&r=0",
        "https://cn.bing.com//th?id=OHR.RedRocksArches_ZH-CN5664546697_UHD.jpg&pid=hp&w=720&h=1280&rs=1&c=4&r=0",
        "https://cn.bing.com//th?id=OHR.LofotenSurfing_ZH-CN5901239545_UHD.jpg&pid=hp&w=720&h=1280&rs=1&c=4&r=0",
      ]
    }
  }
};
</script>

<style>
html,
body {
  height: 100%;
}

body {
  margin: 0;
  background-color: #20262e;
  overflow: hidden;
}

#app .vue-tinder {
  position: absolute;
  z-index: 1;
  left: 0;
  right: 0;
  top: 23px;
  margin: auto;
  width: calc(100% - 20px);
  height: calc(100% - 23px - 65px - 47px - 16px);
  min-width: 300px;
  max-width: 355px;
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

.btns {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 30px;
  margin: auto;
  height: 65px;
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 300px;
  max-width: 355px;
}

.btns img {
  margin-right: 12px;
  box-shadow: 0 4px 9px rgba(0, 0, 0, 0.15);
  border-radius: 50%;
  cursor: pointer;
  -webkit-tap-highlight-color: transparent;
}

.btns img:nth-child(2n + 1) {
  width: 53px;
}

.btns img:nth-child(2n) {
  width: 65px;
}

.btns img:nth-last-child(1) {
  margin-right: 0;
}
</style>