<template>
  <div class="card">
    <div class="card-body">
      <h5 class="card-title">Card title</h5>
      <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card’s content.</p>
      <a href="#" class="btn btn-primary">Go somewhere</a>
    </div>
  </div>
</template>

<script>
export default {
  setup () {
    // 컴포넌트가 사용된 만큼 'setUp()'이 실행된다. 
    console.log('AppCard Setup');

    return {}
  }
}
</script>

<style lang="scss" scoped>

</style>