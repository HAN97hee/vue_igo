
<!--let's go-->
<template>
<div>

  <div class="menu">
    <h3><a v-for="gnb in gnb" :key="gnb">{{ gnb }}</a></h3>
  </div>

  <div class="back" v-if="모달창열 == true">
    <div class="mp">
      <h4>{{ oner[0].content }}</h4>
      <p>{{ oner[0].image }}</p>
      <button @click="모달창열 = false" class="closebtn">close</button>
    </div>
  </div>

  <div>
    <img src="./images/room0.jpg" alt="img1" class="room">
    <h4 @click="모달창열 = true">{{ oner[0].title }}</h4>
    <p>{{ oner[0].price }}</p>
    <button @click="신고수[0] += 1">허위매물신고</button> <span>신고수 : {{ 신고수[0] }}</span> 
  </div>
  <div>
    <img src="./images/room1.jpg" alt="img1" class="room">
    <h4>{{ products[1] }}</h4>
    <p>60만원</p>
    <button @click="신고수[1] += 1">허위매물신고</button> <span>신고수 : {{ 신고수[1] }}</span>
  </div>
  <div>
    <img src="./images/room2.jpg" alt="img1" class="room">
    <h4>{{ products[2] }}</h4>
    <p>40만원</p>
    <button @click="신고수[2] += 1">허위매물신고</button> <span>신고수 : {{ 신고수[2] }}</span>
  </div>

</div>  
</template>


// script area
<script>
import data from './assets/oneroom.js';

export default {
  name: 'App',
  data(){
    return{
      oner : data,
      모달창열 : false,
      price : ['50만원','60만원','70만원'],
      신고수 : [0, 0, 0] ,
      gnb : ['home', 'shop', 'about'],
      products : ['계산동 원룸', '작전동 원룸', '효성동 원룸'],
    }
  },

  methods : {
    numup(){
      this.신고수 += 1;
    },
  },

  components: {
  }
}
</script>


// css area
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu{
  background: darkgoldenrod;
  padding: 15px; 
  border-radius: 5px;
}
.menu a{
  color: #fff;
  padding: 10px;
}

.room{width: 100%;
margin-top: 10px;}

body{
  margin: 0;
}
div{box-sizing: border-box;}
.back{width: 100%; height: 100%; background: rgba(0, 0, 0, 0.5); position: fixed; padding: 20px;}
.mp{width: 100%; background: white; border-radius: 10px; padding: 20px; position: relative;}

h4{cursor: pointer; width: 100px; margin: 0 auto; padding-top: 20px;}
.closebtn{width: 30px; height: 30px; border-radius: 30px; background: none; position: absolute; bottom: 10px; right: 10px; cursor: pointer;}

</style>
