<template>
  <HelloWorld v-if="active" />
  <NewIndex v-else/>
  当前组件是：{{active ?'HelloWorld' :'NewIndex' }}
  <button @click="clickHandler">点击切换组件</button>
</template>
<script>
import HelloWorld from './components/HelloWorld.vue'
import NewIndex from './components/NewIndex.vue'
import { ref ,reactive,computed,onMounted} from "vue";
export default {
  name: 'App',
  components: {
    HelloWorld,NewIndex
  },
  setup(){
    let active = ref(true)
    function clickHandler(){
      active.value = !active.value 
    }
    return{
      active,clickHandler
    }
  }
}
</script>
