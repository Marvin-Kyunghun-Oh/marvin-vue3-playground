<template>
  <div>
    <h2>보간법</h2>
    <p>{{ message }}</p>
    <p v-once>{{ message }}</p>
    <button @click="changeMessage">메시지 변경</button>
    <hr>
    <h2>v-html</h2>
    <p>{{ rawHtml }}</p>
    <p v-html="rawHtml"></p>
    <hr>
    <h2>v-bind</h2>
    <div v-bind:title="dynamicTitle">마우스를 올려보세요.</div>
    <input type="text" value="홍길동" :disabled="isInputDisabled">
    <input v-bind="attrs">
    <hr>
    <h2>JS 표현식</h2>
    <p>{{ 1 + 2 }}</p>
    <p>{{ message.split('').reverse().join('') }}</p>
    <p>{{ message.length > 5 ? '길다' : '짧다' }}</p>
  </div>
</template>

<script>
  import { ref } from 'vue';

  export default {
    setup() {
      // 보간법에 바인딩할 문자열
      const message = ref('안녕하세요!');
      const changeMessage = () => {
        message.value += '!';
      };

      // v-html에 바인딩할 HTML 문자열
      const rawHtml = ref('<strong>안녕하세요!</strong>');

      // v-bind에 바인딩할 문자열
      const dynamicTitle = ref('안녕하세요~~~');
      const isInputDisabled = ref(true);
      const attrs = {
        type: 'password',
        value: '12345676',
        disabled: isInputDisabled
      };

      return {
        message,
        changeMessage,
        rawHtml,
        dynamicTitle,
        isInputDisabled,
        attrs
      };
    },
  };
</script>
