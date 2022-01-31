<template>
  <div>
    <h1>Hello Vue!</h1>
    <h2>{{ age }}</h2>
    <h2>5년 뒤 :: {{ add(5) }}</h2>
    <h2>10년 뒤 :: {{ add(10) }}</h2>
    <h2>15년 뒤 :: {{ add(15) }}</h2>

    <h2>동갑의 30명이 있다면 나이의 총 합은 {{ multiply(age, 30) }}</h2>
    <h2>동갑의 10명이 있다면 나이의 총 합은 {{ multiply(age) }}</h2>
    <h2>{{ getTotalScore(100) }}</h2>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      age: 30,
    };
  },
  methods: {
    add(num) {
      // 화살표 함수 : this 고정
      // 일반 함수 : this가 오브젝트, 즉 객체를 가리킴
      console.log(this);
      return this.age + num;
    },
    // add: (num) => {
    //   // 화살표 함수 : lexical scopte(함수의 선언에 따라 scope 결정)
    //   //              즉, 호출에 영향을 받지 않고 고정된다.
    //   console.log(this);
    //   return this.age + num;
    // },

    multiply(num1, num2 = 10) {
      //num2에 default값 10 부여
      return num1 * num2;
    },

    getTotalScore(num) {
      return this.multiply(num, num);
    },
    // method에서 data에 접근하기 위해서는 this 키워드를 쓰고,
    // 또 다른 method를 접근하기 위해서도 this 키워드를 쓴다.
    // 즉, data가 가진 property들에 접근하기 위해서는 this 키워드를 써야 한다.
  },
};
</script>

<style></style>
