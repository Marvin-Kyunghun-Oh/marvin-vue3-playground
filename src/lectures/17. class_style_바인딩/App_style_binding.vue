<template>
  <div>
    <div :style="styleObjectComputed">
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Obcaecati at enim dolore accusantium nesciunt nulla nemo incidunt ut molestiae officia et, debitis similique aut, reiciendis, saepe tempora voluptates consequatur quam.
    </div>
    <button v-on:click="fontSize++">+</button>
    <button v-on:click="fontSize--">-</button>
  </div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
  setup () {

    // 스타일 속성 반응형 객체로 생성
    const styleObject = reactive({
      color: 'red',
      fontSize: '13px'
    });

    // 계산식이 있는 경우 computed로 구현
    const fontSize = ref(13);
    const styleObjectComputed = computed(() => {
      return {
        color: 'red',
        fontSize: fontSize.value + 'px',
      };
    });


    return {
      styleObject,
      styleObjectComputed,
      fontSize
    }
  }
}
</script>

<style lang="scss" scoped>

</style>