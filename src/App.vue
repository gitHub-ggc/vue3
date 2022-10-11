<template>
  <vite msg="只是一段话" :title="title"></vite>
</template>

<script>
import vite from "./components/vite.vue"
export default {
  name: 'App',
  data(){
    return{
      title:"我会变动的哦"
    }
  },
  created(){
    setTimeout(() => {
      this.title = '我已经变了'
    },2000)
  },
  components: {
    vite
  }
}
</script>
