<template>
    <div>
        <div>{{msg}}</div>
        <div>{{title}}</div>
        <div>得分：{{obj.add}}</div>
        <div>失分：{{obj.bun}}</div>
        <div>总分：{{all}}</div>
        <div>
            <button @click="handleBtn(1)">+</button>
            <button @click="handleBtn(-1)">-</button>
        </div>
    </div>
</template>
<script>
import { watchEffect,ref, reactive, toRefs,computed } from 'vue'
export default{
    props:{
        msg:{
            type:String
        },
        title:String
    },
    setup(props){
       let add = ref(0);
       let bun = ref(0);
       let state = reactive({
        obj:{
            add:10,
            bun:10
        }
       })
       function handleBtn(num){
        // num > 0 ? add.value++ : bun.value--;
        num > 0 ? state.obj.add++ : state.obj.bun--;
       };
       const all = computed(() => {
        console.log(all);
        return (state.obj.add - state.obj.bun) / 100;
       });
       watchEffect(() => {
        console.log(props.title);
       })
       return{
        add,
        bun,
        handleBtn,
        ...toRefs(state),
        all
       }
    }
}
</script>
<style lang="scss" scoped>

</style>