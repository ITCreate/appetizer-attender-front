<template>
  <div class="container">
    <div>
      <div class="hero-image-wrapper">
        <img
          class="hero-image"
          src="~assets/images/main-logo-white.png"
        />
      </div>
      <h1 class="hero-message">今日あなたが飲むのは<br>どのお酒？</h1>
      <ul class="alchole-items">
        <li
          class="alchole-item"
          v-for="alchole in alcoholicBeverages"
          :key="alchole.id"
          @click="redirectSwipe(alchole, $event.target)"
        >
          <span class="alchole-item-name" :src="alchole.name" />
          <img :src="alchole.image" />
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
    };
  },
  created() {
    this.fetchAlcoholicBeverages();
  },
  methods: {
    async fetchAlcoholicBeverages() {
      this.alcoholicBeverages = await this.$axios.$get("/alcoholic_beverages");
    },
    redirectSwipe(alcohol, target) {
      target.parentNode.classList.toggle("action");
      setTimeout(() => {
        target.parentNode.classList.toggle("action");
        this.$router.push({
          name: "swipe",
          params: {
            alcoholicBeverage: alcohol,
          },
        });
      }, 1000);
    },
  },
};
</script>

<style lang="postcss" scoped>
.hero-image-wrapper {
  border-bottom-right-radius: 50%;
  border-bottom-left-radius: 50%;
  padding: 25% 20% 20%;
  background: linear-gradient(to bottom, #ffdce1, #ff7186 80%, #ff7a5c);
}

.hero-image {
  @apply mx-auto;
}

.hero-message {
  @apply my-6 text-center text-2xl font-bold;
  color: #575757;
}

.alchole-items {
  @apply flex flex-wrap mx-4;
}

.alchole-item {
  flex-grow: 1;
  width: 25%;
  max-width: 100px;
  margin: 2% 2%;
  @apply shadow-lg rounded-lg overflow-hidden relative;
}

.alchole-item > img {
  width: 8rem;
  height: 7rem;
  object-fit: cover;
  @apply rounded-lg;
}

.alchole-item-name {
  @apply block my-2 font-bold text-2xl text-white absolute;
  bottom: 1rem;
  left: 1rem;
  text-shadow: 1px 2px 3px #787878;
  z-index: 100;
}

.alchole-item.action {
  transform: scale(1);
  cursor: default;
}

.alchole-item.action::after {
  @apply absolute top-0 right-0 left-0 bottom-0;
  transform: translateX(-100%);
  cursor: default;
  background-image: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0) 0,
    rgba(255, 255, 255, 0.3) 20%,
    rgba(255, 255, 255, 0.4) 60%,
    rgba(255, 255, 255, 0)
  );
  animation: shimmer 1s;
  content: "";
}

@keyframes shimmer {
  100% {
    transform: translateX(100%);
  }
}
</style>