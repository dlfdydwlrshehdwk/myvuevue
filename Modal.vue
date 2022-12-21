<template>
<div class="black-bg" v-if="모달창열렸니 == true">
  <div class="white-bg">
    <img :src="원룸들[누른거].image" alt="">
    <h4>{{원룸들[누른거].title}}</h4>
    <p>{{원룸들[누른거].content}}</p>
    <input v-model="month">
    <!-- 이걸 축약하면 위에처럼 <input @input="month = $event.target.value"> -->
    <p>{{ month }} 개월 이용시 : {{원룸들[누른거].price*month}}원</p>
    <button @click="$emit('bend',모달창열렸니=false)">닫기</button>
    <!-- <button @click="모달창열렸니 = false">닫기</button> -->
  </div>
</div>
</template>

<script>
export default {
    name : 'Modal',
    data(){
      return{
        month : 1,
      }

    },
    watch : {
      month(a){
        if(a>=13){
          alert('1~12까지의 숫자만 입력해주십시오.');
          this.month=1;
        }
        if(isNaN(a)==true){
          alert('1~12까지의 "숫자"만 입력해주십시오.');
          this.month =1;
        }
      }
      /* watch(){ 내용 } : month라는 데이터가 변할때마다 내용코드가 실행됨 
          데이터를 감시하는거 watch:{감시할데이터(){}}*/
          //isNan() 안에는 숫자를 입력하면false 글자를입력하면 true가 나온다
          // input에 입력하면 무조건 string이기 때문에 애매하다
          // 그래서 isNan()이 유용해보인다 
          // 스페이스는 거를 수 없었다고한다.
          // 초기값을 1로하기위해 this.month = 1로 설정 내부에 있는 데이터를
          //사용하려면 this.필수
    },
    props : {
      원룸들 : Array,
      누른거 : Number,
      모달창열렸니 : Boolean
    }

}
</script>

<style>

</style>