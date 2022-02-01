<!--폼 
    : 어떤 입력 양식을 받고, 받은 내용을 서버 등으로 보내 저장하고, 
      일정 형식에 맞는 양식 -->
<template>
  <div>
    {{ user }}
    <h1>{{ user.name }}</h1>
    <hr />
    <form>
      <div>
        <!--IME (Input Method Editor)
        : 자판에 있는 글자보다 수가 많은 문자를 조합하여 입력해주는 시스템
          ==> setValue와 같은 메서드 사용해서 해결 가능-->
        <label for="name">이름</label>
        <input type="text" id="name" v-model="user.name" @input="setValue" />
      </div>
      <div>
        <label for="age">나이</label>
        <input type="number" id="age" v-model="user.age" />
      </div>
      <div>
        <label for="city">사는 곳</label>
        <select id="city" v-model="user.city">
          <option value="seoul">서울</option>
          <option value="daejeon">대전</option>
          <option value="daegu">대구</option>
          <option value="busan">부산</option>
          <option value="gwangju">광주</option>
        </select>
      </div>
      <div>
        <label for="favorite-food">좋아하는 음식</label>
        <select id="favorite-food" multiple v-model="user.favorite">
          <!--multiple 키 : ctrl을 누르고 클릭을 하면 여러 개를 한번에 클릭할 수 있음-->
          <option
            v-for="option in foodOptions"
            :value="option.code"
            :key="option.code"
          >
            {{ option.label }}
          </option>
        </select>
      </div>
      <div>
        <label for="job">직업</label>
        프로그래머<input
          type="checkbox"
          value="programmer"
          v-model="user.job"
        />
        가수<input type="checkbox" value="singer" v-model="user.job" />
        교사<input type="checkbox" value="teacher" v-model="user.job" />
      </div>
      <div>
        <label for="gender">성별</label>
        <input type="radio" value="male" v-model="user.gender" />
        <input type="radio" value="female" v-model="user.gender" />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      foodOptions: [
        { label: "짜장면", code: "JJ" },
        { label: "짬뽕", code: "JB" },
        { label: "탕수육", code: "TS" },
      ],
      user: {
        name: "",
        age: 0,
        city: "seoul",
        favorite: [],
        job: [],
      },
    };
  },
  methods: {
    setValue(e) {
      console.log(e.target.value);
      this.user.name = e.target.value;
    },
  },
};
</script>

<style>
label {
  font-size: 22px;
  font-weight: bold;
  margin-right: 1rem;
}
div {
  margin-bottom: 1rem;
}
</style>
