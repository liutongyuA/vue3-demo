<template>
  <button @click="count++">count is: {{ count }}</button>
  {{ msg }}
  <button @click=greet>点击</button>
</template>

<script>
import { ref ,reactive} from "vue";
export default {
  name: 'HelloWorld',
  // data() {
  //   return {
  //     count: 0
  //   }
  // },
  setup(){
    let count = ref(0)
    let msg = reactive([{a:1,b:2},3])
    let greet = function(event) {
      msg[0].b++
    }
    console.log(count)
    return{count,greet,msg}
  }
}
</script>
