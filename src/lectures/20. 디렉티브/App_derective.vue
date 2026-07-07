<template>
  <div>
    <h1>v-text</h1>
    <p v-text="msg"></p>
    <p>{{ msg }}</p>
    <p v-text="htmlStr"></p>
    <p v-html="htmlStr"></p>
  </div>
  <hr/>

  <div>
    <h1>v-once</h1>
    <p v-once>{{ msg }}</p>
    <button @click="msgChange">msgChange</button>
  </div>
  <hr/>
</template>

<script>
import { ref } from 'vue';

export default {
  setup () {
    // v-text, v-html
    let msg = ref('Hi~');
    const htmlStr = ref('<strong>안녕</strong>');
    
    // v-once 테스트 - v-once는 변경 안됨.
    const msgChange = () => {
      msg.value += "!";
    };

    
    return {
      msg,
      htmlStr,
      msgChange,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>