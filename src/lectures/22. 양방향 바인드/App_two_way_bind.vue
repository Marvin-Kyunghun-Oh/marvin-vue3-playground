<template>
  <div>
    <h1>단방향 바인드를 양방향화</h1>
    <h2>Input Value</h2>
    <input type="text" :value="inputValue" @keyup.enter="onewayBind">
    <br><br>
    <div> {{ inputValue }} </div>
  </div>
  <hr />

  <div>
    <h1>v-model 양방향 바인드 (text, textarea)</h1>
    <h2>text</h2>
    <input type="text" v-model="inputValue">
    <br><br>
    <div> {{ inputValue }} </div>
    <h2>textarea</h2>
    <textarea v-model="inputValueArea"></textarea>
    <br><br>
    <div> {{ inputValueArea }} </div>
  </div>
  <hr />

  <div>
    <h1>v-model 양방향 바인드 (checkbox, radio, select)</h1>
    <h2>checkbox</h2>
    <label for="checkbox">{{ checkboxValue }}</label>
    <input type="checkbox" id="checkbox" v-model="checkboxValue"/>

    <h2>radio</h2>
    <label>
      <input type="radio" name="type" value="O" v-model="radioValue"/>
      O형
    </label>
    <label>
      <input type="radio" name="type" value="A" v-model="radioValue"/>
      A형
    </label>
    <div>{{ radioValue }}</div>

    <h2>select</h2>
    <select v-model="selectValue">
      <option value="html">HTML 수업</option>
      <option value="css">CSS 수업</option>
      <option value="javascript">JavaScript 수업</option>
    </select>
    <div>{{ selectValue }}</div>
  </div>
  <hr />

  <div>
    <h1>v-model 양방향 바인드 (v-model 수식어)</h1>
    <h2>text(lazy)</h2>
    <input type="text" v-model.lazy="inputValue">
    <br><br>
    <div> {{ inputValue }} </div>
    <h2>textarea(number)</h2>
    <textarea v-model.number="inputValueArea"></textarea>
    <br><br>
    <div> {{ inputValueArea }} </div>
    <div> {{ typeof inputValueArea }} </div>
  </div>
  <hr />

</template>

<script>
import { ref } from 'vue';

export default {
  setup () {
    const inputValue = ref(null);

    // 단방향 바인딩 (뷰의 값과 JS의 상태 동기화 추가)
    const onewayBind = (event) => {
      inputValue.value = event.target.value;
    };

    // v-model 양방향 바인드
    const inputValueArea = ref(null);
    const checkboxValue = ref(true);
    const radioValue = ref('O');
    const selectValue = ref('html');


    return {
      inputValue,
      onewayBind,
      inputValueArea,
      checkboxValue,
      radioValue,
      selectValue,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>