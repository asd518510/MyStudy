<template>
  <div>
    <Student name="李四"
             sex="男"
             :age="18"></Student>
  </div>
</template>

<script>
//引入School组件
import Student from './components/Student.vue'

export default {
  name: 'App',
  components: {
    Student
  }
}
</script>

<style>
</style>