<template>

<!-- <div class="black-bg" v-if="모달창열렸니 == true">
  <div class="white-bg">
    <img :src="원룸들[누른거].image" alt="">
    <h4>{{원룸들[누른거].title}}</h4>
    <p>{{원룸들[누른거].content}}</p>
    <p>{{원룸들[누른거].price}}원</p>
    <button @click="모달창열렸니 = false">닫기</button>
  </div>
</div> -->

<!-- <ModalOne :누른거="누른거" :원룸들="원룸들" :모달창열렸니="모달창열렸니"/> -->

<!-- <Modal v-bind:데이터이름="" /> 와 같다. -->


  <!-- <div>
    <h4 :style="스타일">{{products[0]}} 원룸</h4>
    <p>{{ price1 }} 만원</p>
  </div>
  <div>
    <h4 :style="스타일">{{products[1]}} 원룸</h4>
    <p>{{ price2 }}가격은아무거나</p>
  </div>
  <div>
    <h4 :style="스타일">{{products[2]}} 원룸</h4>
    <p>{{ price2 }}가격은아무거나</p>
  </div> -->

  <transition name="fade">
    <Modal @bend="모달창열렸니=false" :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니"></Modal>
  </transition>
  <!-- vue 애니메이션 문법
    1.애니메이션 주고싶은 요소를
    <transition name=:"작명"> 으로 감싸기 
    2. class명을 3개작성
    .작명-enter-from{} -시작스타일
    .작명-enter-active{} -transition
    .작명-enter-to{}  - 끝날때스타일
      퇴장애니메이션 설정은
    .작명-leave-from{}
    .작명-leave-active{}
    .작명-leave-to{} 



   -->

  <!--
    <div class="start" :class="{ end : 모달창열렸니 }">
   <Modal @bend="모달창열렸니=false" :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니"></Modal>
  </div>
  css내용 
    .start{opacity: 0; transition: all 1s;}
    .end{ opacity 1;}  일 때
    
    :class="" 데이터바인딩 :속성="데이터이름" 
  조건이 true일때만 css가 적용되게끔 설정된것
  모달창열렸니가 실행되면 1 ture기 때문에 
  end : true  로 하나 end : 모달창열렸니 로 하나 결과는 같다.
  조건부로 class를 넣는 조건 {클래스명 : 조건}
-->
 
  <div class="menu">
    <a v-for="작명, in 메뉴들" :key="작명">{{작명}}</a>
</div>

<Discount></Discount>

<button @click="priceSort">가격 낮은순 정렬</button>
<button @click="sortBack">되돌리기</button>
<button @click="priceHigh">가격 높은순 정렬</button>
<button @click="ganada">가나다순 정렬</button>

<Card @openmodal="모달창열렸니 =true; 누른거 = $event" :원룸="원룸들[i]" 
 v-for="(작명,i) in 원룸들" :key="작명"></Card>




<!-- <div>
<h4>{{products[0]}}</h4>
<p>{{price[0]}}</p>
<button v-on:click="신고수[0]++">허위매물신고</button>
<span>신고수 : {{신고수[0]}}</span>
</div>
<div>
<h4>{{products[1]}}</h4>
<p>{{price[1]}}</p>
<button v-on:click="신고수[1]++">허위매물신고</button>
<span>신고수 : {{신고수[1]}}</span>
</div>
<div>
<h4>{{products[2]}}</h4>
<p>{{price[2]}}</p>
<button v-on:click="신고수[2]++">허위매물신고</button>
<span>신고수 : {{신고수[2]}}</span>
</div> -->


<!-- <div>
  <img :src="원룸들[0].image" alt="1" class="roomimage">
  <h4 @click="모달창열렸니 =true">{{원룸들[0].title}}</h4>
  <p>{{원룸들[0].price}}원</p>
  <button v-on:click="신고수[0]++">허위매물신고</button>
  <span>신고수 : {{신고수[0]}}</span>
</div>
<div>
  <img :src="원룸들[1].image" alt="1" class="roomimage">
  <h4>{{원룸들[1].title}}</h4>
  <p>{{원룸들[1].price}}원</p>
  <button v-on:click="신고수[1]++">허위매물신고</button>
  <span>신고수 : {{신고수[1]}}</span>
</div>
<div>
  <img :src="원룸들[2].image" alt="1" class="roomimage">
  <h4>{{원룸들[2].title}}</h4>
  <p>{{원룸들[2].price}}원</p>
  <button v-on:click="신고수[2]++">허위매물신고</button>
  <span>신고수 : {{신고수[2]}}</span>
</div> -->

<!-- <div v-for="(a,i) in 원룸들" :key="i">
  <img :src="원룸들[i].image" alt="" class="roomimage">
  <h4 @click="모달창열렸니 = true; 누른거 = i">{{원룸들[i].title}}</h4>
  <p>{{원룸들[i].price}}원</p>
  <button v-on:click="신고수[i]++">허위매물신고</button>
  <span>신고수 : {{신고수[i]}}</span>
</div> -->

</template>
<!-- vue의 for문 작성법1 - 한가지 내용을 반복하고 싶을 때
    <div v-for="작명 in 몇회" :key"작명"></div>
-->
<!-- vue의 for문 작성법2 - 2가지 이상의 내용을 반복하고 싶을 때
  <div v-for="(작명,i) in products" :key="작명" >
  <h4>{{products[i]}}</h4>
  <p>{{price[i]}}</p>
</div>
products : ['역삼동원룸', '천호동원룸', '마포구원룸']
price: ['50만원', '40만원', '30만원']
i는 i++ 이라고 생각하면됨 실행시 다음식을 읽음
products의 내용수 만큼 실행된다 

<div v-for="(a,i) in products" :key="a">
  <h4>{{products[i]}}</h4>
<p>{{price[i]}}</p>
<button v-on:click="신고수[i]++">허위매물신고</button>
<span>신고수 : {{신고수[i]}}</span>
</div>

-->

<!-- 이벤트 다는법
<button v-on:click="신고수++">허위매물신고</button>
<span>신고수 : {{신고수}}</span>

vue에서 이벤트를 실행할때는 v-on:이벤트 를 하는데
v-on: 은 @ 와 의미가 같다 그래서
<button @click="신고수++">허위매물신고</button>
라고 해도 잘 작동된다.
신고수++ 부분은 신고수+=1 이나 신고수 = 신고수 +1 이라고 해도 같다.
v-on 뒤에는 여러가지 이벤트가 사용가능하다
-->

<!-- v-if 문법 더 알아야 할 내용 
  <div v-ir="1 == 1">
    안녕하세요
  </div>
  <div v-else-if="1 == 3">
    안녕하세요2
  </div>
  <div v-else>
    안녕하세요3
  </div>
-->


<script>

import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';



export default {
  name: "App",
  data() {
    return {
      원룸들오리지널 : [...data],
      // array/object데이터의 별개의 사본을 만들려면 [...array자료]
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      price: ['50만원', '40만원', '30만원'],
      메뉴들 : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      스타일 : 'font-size: 20px',
    }
  },
  methods : {
    increase(){
      this.신고수 +=1;
    },
    priceSort(){
      this.원룸들.sort(function(a,b){
        return a.price - b.price
      })
    },
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];
    },
    priceHigh(){
      this.원룸들.sort(function(a,b){
        return b.price-a.price
      })
    },
    ganada(){
      this.원룸들.sort(function(a,b){
        return a.title.toUpperCase() < b.title.toUpperCase()? -1 :1
      })
    },
    // .sort() 문법 설명 작은숫자부터정렬 ㄱㄴㄷ순정렬
    
  },
  components:{
    Discount: Discount,
    Modal: Modal,
    Card : Card,
}
};
// vue에서 함수 만들때 주의사항
// 함수를 만들때는 methods : {}을 만들어주고 그 안에 작성해야함
// 함수안에서 데이터를 만들땐 this.데이터명 으로 할것
// 위 처럼해야 같은 같은 오브젝트안에 있는 데이터를 불러올 수 있다.

</script>

<style>
.fade-enter-from{
/* opacity: 0; */
transform: translateY(-1000px);
}
 /*시작시스타일  */
.fade-enter-active{
  transition: all 1s;
}
/* 애니메이션조건 */
.fade-enter-to{
/* opacity: 1; */
transform: translateY(0px);
}
/* 끝날시스타일 */


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
  
}
.menu a{
  padding: 10px;
  color: aliceblue;
}
.roomimage{
  width: 100%;
  margin-top: 20px;
}
.black-bg{
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding :20px;
}
.white-bg{
  width: 100%; 
  background : white;
  border-radius: 8px;
  padding : 20px;
}
.discount{
  background: #eee;
  padding : 10px;
  margin : 10px;
  border-radius: 5px;
}
</style>



<!-- <template>안에는 html을 짜고
<script>안에는 js짜고
<stlye>안에는 css짜고
node_modules : 프로젝트에 쓰는 라이브러리들
src : 소스코드 담는곳
public : html파일, 기타파일보관하는곳
package.json : 라이브러리 버전, 프로젝트 설정기록하는곳
-->

<!-- 동적인 UI 만드는법 
1. UI의 현재상태를 데이터로 저장해둠
    그 UI가 지금 어떻게 보여아하는가?
2. 데이터에 따라 UI가 어떻게 K보일지 작성
    데이터에 따라 UI가 어떻게 보여야하는지 작성
    데이터가 true면 어떤것이 보이고 false면 어떤것이 보일지
-->