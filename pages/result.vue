<template>
  <div class="container mx-auto">
    <div class="text-center">
      <div class="result mt-4">
        <h1 class="title">RESULT!</h1>
        <p>このツマミが</p>
        <p>お酒に合う！</p>
        <img src="~/assets/images/sample.jpg" class="image">
        <strong>×</strong>
        <img src="~/assets/images/sample2.jpg" class="image">
        <br>
        <strong>♡</strong>
        <br>
        <img src="~/assets/images/sample3.jpg" class="image">
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
export default {};
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