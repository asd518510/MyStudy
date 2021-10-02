<template>
  <div>
    <h2 @click="showName">学校名称：{{name}}</h2>
    <h2>学校地址：{{address}}</h2>
  </div>
</template>

<script>
//引入一个mixin
import { mixin, hunhe2 } from '../mixin'

export default {
  name: 'Shcool',
  data() {
    return {
      name: '小学',
      address: '广州'
    }
  },
  mixins: [mixin, hunhe2]
}
</script>
