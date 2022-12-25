<template>

<div class="bg-black" v-if="모달창 == true">
  <div class="bg-white">
    <img :src="원룸목록[누른거].image" alt="">
    <h3>{{ 원룸목록[누른거].title }}</h3>
    <p>가격 : {{ 원룸목록[누른거].price }}</p>
    <p>{{ 원룸목록[누른거].content }}</p>
    <p>{{ 원룸목록[누른거].size }}</p>
    <button @click="모달창 = false">닫기</button>
  </div>
</div>






 <div v-for="(rooms,i) in 원룸목록" :key="i">
  <img :src="원룸목록[i].image" alt="">
  <h3 @click="모달창 = true; 누른거 = i">{{ 원룸목록[i].title }}</h3>
  <p>가격 : {{ 원룸목록[i].price }}</p>
  <p>{{ rooms.content }}</p>
  <p>{{ 원룸목록[i].size }}</p>
 </div>
 
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import onerooms from './assets/onerooms';



export default {
  data(){
    return{
      원룸목록 : onerooms,
      누르면 : 0,
      모달창 : false,
    }
    
  },
  components: {
   
  }
}
</script>

<style>
*{
  margin: 0px;
  padding: 0px;
}
.bg-black{
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.356);
  position: fixed;
  padding: 20px;
}
.bg-white{
  width: 100%;
  padding: 20px;
  background-color: white;
  border-radius: 15px;
}

</style>
