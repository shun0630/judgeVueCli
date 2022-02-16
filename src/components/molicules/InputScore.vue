<template>
    <h2>得点入力フォーム</h2>
    <h3>ジャッジ中のチーム</h3>
    <img v-bind:src="team_image_path" width="300" height="200"><br>
    <span>チーム選択</span>
    <select @change="input_team" v-model="selectedTeamName">
        <option v-for="team in team_list" :key="team.appearance_order" v-bind:value="team.team_name">
            {{ team.team_name }}
        </option>
    </select><br>
    <span>得点入力</span>
    <input type="number" min="0" max="20" @input="changeScore" v-model="inputScore"><br>
    <MyButton
    @click="this.submitScore">得点入力</MyButton>

    <MyButton
    @click="submitAllScore">全チームジャッジ終了</MyButton>

</template>

<script>
import MyButton from "../atmos/button.vue"
export default {
    components:{
        MyButton
    },
    props:["team_list"],
    data(){
        return{
            selectedTeamName: '',
            inputScore: 0
        }
    },
    methods: {
        submitScore: function(){
            console.log(this.selectedTeamName, this.inputScore);
            this.$emit("submit-score", this.selectedTeamName, this.inputScore)
        },
        submitAllScore: function(){
            this.$emit("submit-all-score")
        },
        changeScore: function(){
            console.log(this.inputScore)
            this.$emit("change-score", this.inputScore)
        }

    }

};
</script>