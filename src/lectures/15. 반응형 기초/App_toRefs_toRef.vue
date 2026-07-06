<template>
  <div>
    <p>author: {{ author }}</p>
    <p>title: {{ title }}</p>
  </div>
</template>

<script>
import { reactive, toRef, toRefs } from 'vue';

export default {
  setup () {

    // 반응형 객체 - 구조분해할당 테스트
    const book = reactive({
      author: 'Vue Team',
      year: '2020',
      title: 'Vue 3 Guide',
      description: '당신은 이 책을 지금 바로 읽습니다',
      price: '무료'
    })

    // 구조분해할당 된 속성은 반응형을 잃는다.
    // const { author, title } = book

    // toRef(), toRefs()를 사용하면 구조분해할당을 해도 반응형을 유지
    const { author, title } = toRefs(book);
    const descriptionRef = toRef(book, 'description');

    return {author, title, book, descriptionRef};
  }
}
</script>
