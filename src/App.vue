<template>
  <HelloWorld v-if="active" />
  <NewIndex v-else :toxun='toxun' @emitEvent="emitEvent"/>
  当前组件是：{{active ?'HelloWorld' :'NewIndex' }}
  <button @click="clickHandler">点击切换组件</button>
  <br>
  子组件数据{{ zi }}
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
    let toxun = ref('父组件的数据')
    let zi = ref(null)
    function clickHandler(){
      active.value = !active.value 
    }
    const emitEvent =e=>{
      zi.value = e
    }
    return{
      active,clickHandler,toxun,emitEvent,zi
    }
  }
}
</script>
