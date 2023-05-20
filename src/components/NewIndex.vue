<template>
    {{ toxun }}
    <button @click="greet">点击</button>
    <!-- <button @click="btn">点击</button> -->
    <button @click="count.id++">count</button>
  </template>
  
  <script setup>
  import { ref ,reactive,computed,onMounted,watch,watchEffect} from "vue";

      let count = ref({
        id:0
      })

      
      let msg = reactive([{a:1,b:2},3,{hh:'wc'}])
      let greet = function(event) {
        // msg[0].b++
        // msg[2].hh = 'nm'
        author.obj = {id:1,t:2}
      }
      const author = reactive({
        name: 'John Doe',
        obj:{id:0,t:2},
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

      watch(()=>author,()=>{
        console.log('改变了')
      },{deep:true})
      watch(count,()=>{
        console.log('count改变了')
      },{deep:true})

      watch(()=>author.name,()=>{
        console.log('改变了')
      })
      watchEffect(()=>{
        // console.log('什么执行')
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
      const emit = defineEmits(['emitEvent'])
      const btn = ()=>{
        emit('emitEvent',msg)
      }
  </script>
  