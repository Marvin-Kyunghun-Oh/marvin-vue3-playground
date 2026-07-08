<template>
  <div>
    <!-- 컴포넌트 사용 -->
    <TheNav></TheNav>
    <TheView></TheView>
  </div>
</template>

<script>
import TheNav from './components/TheNav.vue';
import TheView from './components/TheView.vue';

export default {
  // 컴포넌트 지역등록
  components: {
    TheNav,
    TheView,
  },
  setup () {
    return {}
  }
}
</script>

<style lang="scss" scoped>

</style>