<template>
  <div>
    <h1>watchEffect를 통해 글을 저장했을 때 자동으로 저장하도록 한다.</h1>
    <form action="" @submit.prevent="save(title, contents)">
      <input type="text" v-model.lazy="title" placeholder="입력하세요."/><br>
      <textarea v-model.lazy="contents" placeholder="입력하세요..."></textarea>
      <hr />
      <button>저장</button>
    </form>
  </div>
</template>

<script>
import { ref, watchEffect } from 'vue';

export default {
  setup () {
    
    const title = ref('');
    const contents = ref('');

    const save = (title, contents) => {
      console.log(`자동저장. title: ${title}, contents: ${contents}`);
    };

    watchEffect(() => {
      save(title.value, contents.value);
    });

    return {
      title,
      contents,
      save,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>