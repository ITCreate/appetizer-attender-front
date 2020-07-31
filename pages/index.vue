<template>
  <div class="container">
    <div>
      <p class="background">
        <img src="~assets/image/main-logo-white.png">
        <h1>
          今日のあなたはどのお酒？
        </h1>
      </p>
      <button @click=""><img src="~assets/image/drink_beer.png" width="100" height="100">ビール</button>
      <button @click=""><img src="~assets/image/drink_nihonsyu.png" width="100" height="100">日本酒</button>
      <button @click=""><img src="~assets/image/party_highball_glass.png" width="100" height="100">ハイボール</button><br>
      <button @click=""><img src="~assets/image/red_wine.png" width="100" height="100">赤ワイン</button>
      <button @click=""><img src="~assets/image/white_wine.png" width="100" height="100">白ワイン</button>
      <button @click=""><img src="~assets/image/drink_cocktail.png" width="100" height="100">カクテル</button>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.background {
  background-color: #ef93b6
}
</style>
