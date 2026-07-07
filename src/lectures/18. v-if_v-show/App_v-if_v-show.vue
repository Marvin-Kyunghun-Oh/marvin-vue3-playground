<template>
  <div>
    <h1>v-if</h1>
    <h2 v-if="visible">Hello Vue3</h2>
    <h2 v-else>false 입니다.</h2>
    <button @click="visible = !visible">toggle</button>
    <hr />
    <template v-if="visible">
      <h1>v-if 템플릿화</h1>
      <p>Paragraph 1</p>
      <p>Paragraph 2</p>
    </template>
    <hr />
    
    <h1>v-if-else-if-else</h1>
    <h2 v-if="type === 'A'">A타입</h2>
    <h2 v-else-if="type === 'B'">B타입</h2>
    <h2 v-else>No타입</h2>
    <button @click="type = 'A'">A</button>
    <button @click="type = 'B'">B</button>
    <button @click="type = ''">NO</button>
    <hr/>

    <h1>v-Show</h1>
    <h2 v-show="show">V-Show!!</h2>
    <button @click="show = !show">show toggle</button>
    
  </div>
</template>

<script>
import {ref} from 'vue'

export default {
  setup () {
    // v-if/else로 조건부 렌더링
    const visible = ref(true);

    // v-else-if로 조건부 렌더링
    const type = ref('A');

    // v-show로 조건부 렌더링
    const show = ref(true);

    return {
      visible,
      type,
      show,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>