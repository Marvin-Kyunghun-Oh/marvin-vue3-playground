<template>
  <div>
    <h1></h1>
    <p>{{ message }}</p>
    <p>{{ reversMessage }}</p>
  </div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
  setup () {
    const message = ref('Hello Vue3');
    const reversMessage = ref('');

    // watch -> immediate 옵션 테스트
    watch(message, (newValue) => {
      console.log('즉시실행');
      reversMessage.value = newValue.split('').reverse().join('');
    }, 
    {immediate: true});

    
    // watch 로직 함수로 분리, 즉시 실행
    const reverseFuction = newValue => {
      console.log('즉시실행22');
      reversMessage.value = newValue.split('').reverse().join('');
    };
    watch(message, reverseFuction);
    reverseFuction(message.value); // 즉시 실행

    const reverseFuction2 = () => {
      console.log('즉시실행33');
      reversMessage.value = message.value.split('').reverse().join('');
    };
    watch(message, reverseFuction);
    reverseFuction2(); // 즉시 실행


    return {
      message,
      reversMessage
    }
  }
}
</script>

<style lang="scss" scoped>

</style>