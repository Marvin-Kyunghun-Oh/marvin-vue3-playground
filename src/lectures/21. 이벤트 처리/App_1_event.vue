<template>
  <div>
    <h1>v-on 이벤트 호출 시 어떤 매개변수를 받는지??</h1>
    <button @click="printEventInfo">버튼</button>
    <br>
    <input type="text" @keyup="onKeyupHandler" />
    <hr/>

    <h1>v-on 이벤트 인라인 핸들링</h1>
    <button @click="printEventInfo2('hello~', $event)">버튼</button>
    <hr/>
    
  </div>
</template>

<script>
export default {
  setup () {
    
    // v-on 이벤트 호출
    const printEventInfo = (event) => {
      console.log('event : ', event);
      console.log('event.target : ', event.target);
      console.log('event.target.tagName : ', event.target.tagName);
    };
    const onKeyupHandler = event => {
      console.log('event.key : ', event.key);
    };

    // v-on 이벤트 객체 접근
    const printEventInfo2 = (message, event) => {
      console.log('message : ', message);
      console.log('event : ', event);
      console.log('event.target : ', event.target);
      console.log('event.target.tagName : ', event.target.tagName);
    };
    

    return {
      printEventInfo,
      printEventInfo2,
      onKeyupHandler,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>