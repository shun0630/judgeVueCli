<template>
    <h2>ジャッジ名選択</h2>
    <select v-model="selected_judge">
        <option v-for="judge in judges" :key="judge">
            {{ judge }}
        </option>
    </select><br>
    <MyButton
    @click="this.selectJudgeButton"
    >ジャッジ選択</Mybutton>
</template>

<script>
import MyButton from "../atmos/button.vue"
export default {
    name: "judgeSelect",
    components:{
        MyButton
    },
    props: ["judges"],
    data: function(){
        return{
            selected_judge: "",
            if_judge: false
        }
    },
    methods: {
        selectJudgeButton: function(){
            console.log(this.selected_judge);
            this.if_judge = true
            this.$emit("judge-button", this.selected_judge);
            
        }
    }
}
</script>