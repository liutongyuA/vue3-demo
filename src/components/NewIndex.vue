<template>
    {{ toxun }}
  </template>
  
  <script setup>
  import { ref ,reactive,computed,onMounted,watch,watchEffect,defineProps} from "vue";
      let count = ref(0)
      let msg = reactive([{a:1,b:2},3,{hh:'wc'}])
      let greet = function(event) {
        // msg[0].b++
        // msg[2].hh = 'nm'
        author.name = 'mock'
      }
      const author = reactive({
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ],
        bage: computed(()=>{
          return count.value+1
        })
      })
      const isBook = computed(()=>{
        return author.books.length > 0 ? 'Yes' : 'No'
      })
      watch(()=>author.name,()=>{
        console.log('改变了')
      })
      watchEffect(()=>{
        console.log('什么执行')
      })
      onMounted(()=>{
        console.log(isBook.value+'ghg',author.bage)
      })
      //接受props
      defineProps({
        toxun:{
          type:String,
          default:'哈哈哈'
        }
      })
  </script>
  