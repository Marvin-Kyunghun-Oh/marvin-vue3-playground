<template>
  <div>
    <h1> 스크립트에서 키보드 이벤트 제어 <br>(엔터 눌렀을 때만 추가) </h1>
    <input type="text" @keyup="addTodo" />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
      </li>
    </ul>
    <hr/>

    <h1> v-on으로 엔터 제어 <br>(엔터 눌렀을 때만 추가) </h1>
    <input type="text" @keyup.enter="addTodoVOn" />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
      </li>
    </ul>
    <hr/>
  </div>
</template>

<script>
import { reactive } from 'vue';

export default {
  setup () {
    
    const todos = reactive([]);
    const addTodo = (event) => {
      if (event.key === 'Enter') {
        todos.push(event.target.value);
        initText(event);
      }
    };

    const addTodoVOn = (event) => {
      todos.push(event.target.value);
      initText(event);
    }

    const initText = (event) => {
      event.target.value = '';
      event.target.focus();
    }

    return {
      todos,
      addTodo,
      addTodoVOn
    }
  }
}
</script>

<style lang="scss" scoped>

</style>