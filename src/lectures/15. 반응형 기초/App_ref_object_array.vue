<template>
  <div>

  </div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
  setup () {

    // ref -> Object
    const count = ref(0);
    const state = reactive({
      count,
    });
    console.log(count.value);
    console.log('state.count:', state.count); // .value 없이도 값을 가져온다.

    // ref -> array
    const message = ref('Hello');
    const arr = reactive([message]);
    console.log('arr.message : ', arr[0].value); // .value 붙여야 됨.


    return {
      count,
      state
    }
  }
}
</script>
