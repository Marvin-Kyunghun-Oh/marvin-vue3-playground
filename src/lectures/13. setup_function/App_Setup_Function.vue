<template>
  <div>
    <p>{{ counter }}</p>
    <p>{{ message }}</p>
    <button @click="increment">Increment</button>
  </div>
</template>

<script>
  import { ref } from 'vue'

  export default {
    setup() {
      const counter = ref(0);
      const message = ref('Hello, Vue 3');
      const increment = () => {
        counter.value++;
      };

      // setup() 함수에서 반환된 값들은 템플릿에서 사용할 수 있다.
      return {
        counter,
        message,
        increment
      }
    },
    mounted() {
      // Options API의 mounted() 훅에서 this를 사용하여 data 속성에 접근할 수 있다.
      console.log('mounted() counter:', this.counter);
    }

  }
</script>
