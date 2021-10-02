<template>
  <div>
    <Student></Student>
    <hr />
    <School></School>
  </div>
</template>

<script>
//引入Student组件
import Student from './components/Student.vue'

//引入Student组件
import School from './components/School.vue'

export default {
  name: 'App',
  components: {
    Student,
    School
  }
}
</script>

<style>
</style>