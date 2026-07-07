<template>
  <div>

  </div>
</template>

<script>
import {reactive, ref, watch} from 'vue';

export default {
  setup () {
    
    // watch 함수를 통해 특정 테이터가 변경됨을 감지해서 다른 작업을 할 수 있다.
    const message = ref('');
    watch(message, (newValue, oldValue) => {
      console.log('newValue : ', newValue);
      console.log('oldValue : ', oldValue);
    });


    // watch 함수의 또다른 사용법
    const x = ref(0);
    const y = ref(0);
    watch (
      () => x.value + y.value,
      (newValue, oldValue) => {
        //console.log('sum: ', newValue);
        //console.log('bf: ', oldValue);
      }
    );

    // watch => 여러 개 감지 (배열로 처리)
    watch([x,y], ([newX, newY]) =>{
      console.log('newX: ', newX);
      console.log('newY: ', newY);
    });

    
    // watch => 객체타입에 사용
    const obj = reactive({
      count: 0,
    });
    
    // 객체의 경우 oldValue, newValue 같은 객체를 바라본다.
    watch(obj, (newValue) => {
      console.log('newValue: ', newValue.count);
    });

    // 객체의 요소를 감지할때는 '() =>' 앞에 붙여야 반응형으로 인식
    watch(() => obj.count, (newValue, oldValue) => {
      //console.log('newValue: ', newValue);
      //console.log('oldValue: ', oldValue); 
    });


    

    return {
      message,
      x,
      y,
      obj,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>