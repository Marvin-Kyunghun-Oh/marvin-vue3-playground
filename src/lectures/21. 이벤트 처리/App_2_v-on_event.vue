<template>
  <div>
    <h1>이벤트 전파 예시</h1>
    <div id="modifiers">
      <div @click="clickDiv">
        DIV 영역 (디렉티브로 이벤트 전파 방지)
        <p @click.stop="clickP">
          P 영역 (함수에 이벤트 전파 방지 구현)
          <span @click="clickSpan">Span 영역</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  setup () {
    
    // Span 영역 클릭 시 => clickP, clickDiv도 호출됨...
    // => 이벤트 전파
    // => 이벤트 전파를 막기 위해 `event.stopPropagation()` 선언.
    // => 'p'의 경우 v-on 디렉티브를 통해 이벤트 전파 막음.
    const clickDiv = () => {
      console.log('clickDiv');
    }
    const clickP = () => {
      console.log('clickP');
    }
    const clickSpan = (event) => {
      console.log('clickSpan');
      
      // 이벤트 전파 막기
      event.stopPropagation();
    }

    return {
      clickDiv,
      clickP,
      clickSpan
    }
  }
}
</script>

<style scoped>
#modifiers div,
#modifiers p,
#modifiers span {
  padding: 40px;
}

#modifiers div {
  background: #ccc;
}
#modifiers p {
  background: #999;
}
#modifiers span {
  background: #666;
  display: block;
}
</style>