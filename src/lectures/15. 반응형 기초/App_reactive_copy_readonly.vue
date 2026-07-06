<template>
  <div>
    <p>original.count: {{ original.count }}</p>
    <p>copy.count: {{ copy.count }}</p>
  </div>
</template>

<script>
import { reactive, readonly } from 'vue'

export default {
  setup () {

    // readonly() - reactive 객체를 읽기 전용으로 만든다.
    const original = reactive({
      count: 0,
    });
    const copy = readonly(original);

    original.count++;
    copy.count++; // readonly 객체는 값을 변경할 수 없다. (에러 발생)

    return {
      original,
      copy,
    }
  }
}
</script>
