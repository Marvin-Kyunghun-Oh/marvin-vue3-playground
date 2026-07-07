<template>
  <div>
    <h2>{{ teacher.name }}</h2>
    <h3>강의가 있습니까?</h3>
    <!-- <p>{{ teacher.subject.length > 0 ? "Yes" : "No" }}</p> -->
    <p>{{ hasSubject }}</p>
    <p>{{ existSubject() }}</p>
    <h2>이름은?</h2>
    <p>{{ fullName }}</p>
  </div>
</template>

<script>
import { ref, reactive, computed } from 'vue';

export default {
  setup () {
    const teacher = reactive({
      name: 'John Doe',
      subject: ['Math', 'Science', 'History'],
    });


    // Computed를 통한 계산 결과 바인딩
    const hasSubject = computed(() => {
      console.log('Computed function executed');
      return teacher.subject.length > 0 ? "Yes" : "No";
    });

    // Method를 통한 계산 결과 바인딩
    const existSubject = () => {
      console.log('Function executed');
      return teacher.subject.length > 0 ? "Yes" : "No";
    }
    // => Computed는 값을 캐싱하기 때문에 더 빠르다.


    // Writeable computed를 통한 Getter/Setter 구현    
    const firstName = ref('John');
    const lastName = ref('Doe');
    const fullName = computed(() => {
      return firstName.value + " " + lastName.value;
    });

    console.log('console 출력 : ', fullName.value);

    // computed는 기본적으로 getter 전용이라, 경고 발생!
    fullName.value = 'Jane Smith';


    // Writeable computed를 통한 Getter/Setter 구현
    const writeableFullName = computed({
      get() {
        return firstName.value + " " + lastName.value;
      },
      set(value) {
        console.log('value : ', value);
        const [first, last] = value.split(' ');
        firstName.value = first;
        lastName.value = last;
      },
    });

    // Writeable computed의 setter를 통해 값 변경
    writeableFullName.value = 'Jane Smith';
    console.log('console 출력(writeable) : ', writeableFullName.value);


    
    return { 
      teacher,
      hasSubject,
      existSubject,
      fullName,
      writeableFullName,
    }
  }
}
</script>
