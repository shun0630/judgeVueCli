<template>
  <h2>得点入力フォーム</h2>
  <h3>ジャッジ中のチーム</h3>
  <img v-bind:src="team_image_path" width="300" height="200"><br>
  <span>チーム選択</span>
  <select @change="input_team" v-model="select_score_team_name">
      <option v-for="option in options"  v-bind:key="option.team_name">
        {{ option.team_name }}
      </option>
  </select><br>
  <span>得点入力</span>
  <input type="number" min="0" max="20" @input="input_score" v-model="select_score">
  <br>
  <button v-on:click="input_score_submit">得点の確定</button><br>
  <button v-on:click="input_all_score_submit">全チームジャッジ終了</button>
</template>

<script>
export default {
  name: 'ScoreInputForm',
  props: {
  },
  data(){
    return {
      select_score_team_name: '',
      select_score: '',
      options: [
        { appearance_order: 0, team_name: "test1", score: 0 },
        { appearance_order: 0, team_name: "test2", score: 0 },
        { appearance_order: 0, team_name: "test3", score: 0 },
      ],
      team_image_path: ""
    }
  },
  methods: {
    input_score_submit: function(){
      console.log("input_score_submit")
    },
    input_all_score_submit: function(){
      console.log("input_all_score_submit")
    },
    input_score: function(){
      console.log("input_score")

    },
    input_team: function(){
      console.log("input_team")
    }
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
