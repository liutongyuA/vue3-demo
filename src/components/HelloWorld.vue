<template>
  <button @click="count++">count is: {{ count }}</button>
  {{ msg }}
  <button @click=greet>点击</button>
  {{isBook}}
</template>

<script>
import { ref ,reactive,computed,onMounted} from "vue";
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
    const author = reactive({
      name: 'John Doe',
      books: [
        'Vue 2 - Advanced Guide',
        'Vue 3 - Basic Guide',
        'Vue 4 - The Mystery'
      ]
    })
    const isBook = computed(()=>{
      return author.books.length > 0 ? 'Yes' : 'No'
    })
    onMounted(()=>{
      console.log(isBook.value+'ghg')
    })
    return{count,greet,msg,isBook}
  }
}
</script>
