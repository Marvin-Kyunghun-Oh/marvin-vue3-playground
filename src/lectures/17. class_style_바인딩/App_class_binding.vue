<template>
  <div>
   <!-- 
      <div class="text" :class="{ 'active': isActive, 'text-danger': hasError }"> 텍스트 입니다. </div>
      <div class="text" :class="classObject"> 텍스트 입니다. </div>
      <div class="text" :class="computedClassObject"> 텍스트 입니다. </div>
    -->
      <div class="text" :class="[activeClass, errorClass]"> 텍스트 입니다. </div>
      <button @click="toggle">Toggle</button>
      <button @click="toggleError">Toggle Error</button>
  </div>
</template>

<script>
import { ref, reactive, computed } from 'vue';

export default {
  setup () {

    // class 바인딩을 통한 조건부 스타일링
    const isActive = ref(true);
    const toggle = () => {
      isActive.value = !isActive.value;
    }
    const hasError = ref(false);
    const toggleError = () => {
      hasError.value = !hasError.value;
    }

    // 클래스 속성 반응형 객체로 생성하여 바인딩
    const classObject = reactive({
      active: isActive,
      'text-danger': hasError
    });
    
    // 클래스 속성 반응형 객체로 생성하여 바인딩 => computed
    const computedClassObject = computed(() => {
        return {
          active: true && true,
          'text-danger': true && true,
        };
    });

    // 클래스 속성 반응형 배열로 생성하여 바인딩
    const activeClass = ref('active');
    const errorClass = ref('error');
    

    return {
      isActive,
      toggle,
      hasError,
      toggleError,
      classObject,
      computedClassObject,
      activeClass,
      errorClass,
    }
  }
}
</script>


<style scoped>
.active {
  font-weight: 900;
}
.text-danger {
  color: red;
}
</style>