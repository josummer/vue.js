<template>
  <div>
    <h1>Hello {{ name }}!</h1>
    <button v-on:click.middle="changeName">change name</button>
    <!--<modifier> 클릭 left는 default / 
        middle : 가운데 휠 클릭, right : 오른쪽 휠 클릭-->
    <button
      v-on:mouseover="name = 'Code Scalper'"
      v-on:mouseleave="name = 'Scalper'"
    >
      change name
    </button>
    <a v-on:click.prevent="movePage" href="https://naver.com">naver로 이동</a>
    <h2>{{ number }}</h2>
    <button v-on:click="increment($event, 1)">숫자 1 증가</button>
    <button v-on:click="decrement(1)">숫자 1 감소</button>
    <button v-on:click="increment(5)">숫자 5 증가</button>
    <button v-on:click="decrement(5)">숫자 5 감소</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "Scalper",
      number: 0,
    };
  },
  methods: {
    changeName() {
      this.name = "Code Scalper";
    },
    movePage() {
      //e.preventDefault(); // 기본적으로 탑제되있는 페이지 이동 기능을 막아줌
      // parameter로 e 줘야 함 (지금은 위에 쓰느냐 생략)
      const check = confirm("페이지를 이동하시겠습니까?");
      if (check) {
        console.log("page 이동");
      } else {
        console.log("page 이동안함");
      }
    },
    increment(e, num) {
      console.log(e);
      this.number += num;
    },
    decrement(num) {
      this.number -= num;
    },
  },
};
</script>

<style>
a {
  font-size: 24px;
  display: block;
}
</style>
