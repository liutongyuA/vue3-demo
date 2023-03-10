<template>
    <button @click="count++">count is: {{ count }}</button>
    {{ msg }}
    <button @click=greet>点击</button>
    {{isBook}}
  </template>
  
  <script setup>
  import { ref ,reactive,computed,onMounted} from "vue";
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
  </script>
  