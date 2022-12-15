<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div>
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
  </div>
</template>

<script>

export default {
  name: "App",
  data() {
    return {
      price1: 80,
      price2: 70,
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      스타일 : 'font-size: 20px',
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
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
