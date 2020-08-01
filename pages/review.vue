<template>
  <div class="container mx-auto">
    <div class="combo-set">
      <h1 class="title">　＜　　　　　<img src="~assets/image/food_edamame.png">×<img src="~assets/image/kunsei_cheese.png">×<img src="~assets/image/drink_nihonsyu.png"></h1>
    </div>
    <div class="comment-window">
      <img src="~assets/image/animal_panda.png">　以外に合う！　★×5<br>
      <img src="~assets/image/icon_others_08.png">　さすがに合わん...　★×1<br>
      　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　まあまあかな...　★×2　<img src="~assets/image/animal_hiyoko.png">
    </div>
    <div class="eval-star">
      タップして評価<br>
      ★★★☆☆
    </div>
    <div class="comment-send">
    <input type="text" name="CommentInput" size="50">　<input type="button" value="送信">
    </div>
  </div>

</template>

<script>
export default {};
</script>

<style>
.title{
  width: 768px;
  height: 100px;
  border: solid;
  font-size: 30px;
}
.title img{
  display: inline;
  margin: 20px;
  width: auto;
  height: 75px;
  margin: 20px;
}
.comment-window{
  width: 768px;
  height: 500px;
  border: solid;
}
.comment-window img{
  display: inline;
  width: auto;
  height: 50px;
  margin: 40px 20px;
}
.eval-star{
  width: 768px;
  height: 150px;
  border: solid;
  text-align: center;
  font-size: 50px;
}
.comment-send{
  width: 768px;
  height: 100px;
  border: solid;
  text-align: center;
  line-height: 50px;

}
</style>
