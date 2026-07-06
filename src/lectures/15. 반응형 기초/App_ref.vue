<template>
  <div>
    <p>{{ message }}</p>
    <button @click="addMessage">Click Me</button>
    <p>{{ reactiveMessage.message }}</p>
    <button @click="addReactiveMessage">reactiveMessage - Click Me</button>
    <p>{{ refMessage }}</p>
    <button @click="addRefMessage">refMessage - Click Me</button>
  </div>
</template>

<script>
  import { reactive, ref } from 'vue';

  export default {
    setup() {
      // Reactive에 기본타입 선언 시 동작하지 않는다.
      let message = reactive('Hello, Vue!');
      const addMessage = () => {
        message += '!';
      };
      console.log(message);

      // Reactive에 기본타입 선언하려면 아래와 같이...
      let reactiveMessage = reactive({ message: 'Hello, Vue!' });
      const addReactiveMessage = () => {
        reactiveMessage.message += '!';
      };
      console.log(reactiveMessage);

      // 기본타입은 그냥 ref를 사용하면 된다.
      let refMessage = ref('Hello, Vue!');
      const addRefMessage = () => {
        refMessage.value += '!';
      };
      console.log(refMessage);

      return {
        message,
        addMessage,
        reactiveMessage,
        addReactiveMessage,
        refMessage,
        addRefMessage
      };
    }
  };
</script>

