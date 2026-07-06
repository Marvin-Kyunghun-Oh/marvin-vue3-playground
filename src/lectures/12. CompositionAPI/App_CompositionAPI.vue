<template>
  <div>
    <h2>반응형 메시지</h2>
    <p>{{ reactiveMessage }}</p>
    <button @click="addReactiveMessage">Add Message</button>
     <h2>일반 메시지</h2>
     <p>{{ normalMessage }}</p>
     <button @click="addNormalMessage">Add Message</button>
  </div>
</template>

<script>
  import { ref, isRef, onMounted, onBeforeMount } from 'vue'

  export default {
    setup() {
      console.log('setup() is called');

      // 반응형 : ref()를 통한 반응형 테스트
      const reactiveMessage = ref('Hello, Reactive');
      const addReactiveMessage = () => {
        reactiveMessage.value += '!'
      };
      //console.log('reactiveMessage is ref:', isRef(reactiveMessage)); // true

      // 반응형 : 일반 문자열을 통한 반응형 테스트
      let normalMessage = "Hello, Normal";
      const addNormalMessage = () => {
        normalMessage += '!'
      };
      //console.log('normalMessage is ref:', isRef(normalMessage)); // false

      // 라이프사이클 훅
      onBeforeMount(() => {
        console.log('onBeforeMount() is called');
      })
      onMounted(() => {
        console.log('onMounted() is called');
      })

      return {
        reactiveMessage,
        normalMessage,
        addReactiveMessage,
        addNormalMessage,
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>
