<template>
  <div>
    목록 렌더링
    <ul>
      <li v-for="(item, index) in items" :key="item.id">
        인덱스: {{index}}, {{ item.message }}
      </li>
    </ul>
  </div>
  <hr />

  <div>
    목록 렌더링 (짝수 ID만)
    <ul>
      <template v-for="(item, index) in items" :key="item.id">
        <li v-if="item.id % 2 === 0">
          ID: {{ item.id }}, 인덱스: {{index}}, {{ item.message }}
        </li>
      </template>
    </ul>
  </div>
  <hr />

  <div>
    목록 렌더링 (짝수 ID만, Computed)
    <ul>
      <template v-for="(item, index) in evenItems" :key="item.id">
        <li> ID: {{ item.id }}, 인덱스: {{index}}, {{ item.message }}</li>
      </template>
    </ul>
  </div>
  <hr />

  <div>
    객체 속성 렌더링
    <ul>
      <li v-for="(value, key, index) in myObject" :key="key">
        {{ index }} - {{ key }} - {{ value }}
      </li>
    </ul>
  </div>
</template>

<script>
import { computed, reactive } from 'vue';

export default {
  setup () {
    // v-for를 통한 목록 렌더링
    const items = reactive([
      {id: 1, message: 'Java'},
      {id: 2, message: 'HTML'},
      {id: 3, message: 'CSS'},
      {id: 4, message: 'JavaScript'},
    ]);

    // computed를 통한 계산식 바인딩
    const evenItems = computed(() => 
      items.filter(item => item.id % 2 === 0)
    );

    // v-for를 통한 객체 속성 렌더링
    const myObject = reactive({
        title: '제목',
        author: '홍길동',
        amount: 10000,
    });

    return {
      items,
      evenItems,
      myObject,
    }
  }
}
</script>
