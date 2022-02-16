<template>
<div class="main">
<h2>メインコンポーネント</h2>
  <SelectJudge 
    v-if="!if_judge" 
    v-bind:judges="judges_list"
    @judge-button="selectJudge"
    ></SelectJudge>
  <h2 v-if="if_judge">{{judge}}様がジャッジ中</h2>
  
  <TeamTable 
  v-if="if_judge" 
  :items="nearTeams"
  ></TeamTable>

  <InputScore 
  v-if="if_judge"
  :team_list="dataTeams"
  @submit-score="submitScore"
  @submit-all-score="submitAllScore"
  @change-score="changeScore"
  ></InputScore>


  <TeamTable 
  v-if="if_judge" 
  :items="dataTeams"
  ></TeamTable>

</div>
</template>

<script>
import SelectJudge from '../molicules/SelectJudge.vue'
import InputScore from '../molicules/InputScore.vue'
import TeamTable from '../molicules/TeamTable.vue'

export default {
  name: 'ScoreInputForm',
  components: {
    SelectJudge,
    InputScore,
    TeamTable
  },
  props: {
  },
  data(){
    return {
      select_score_team_name: '',
      select_score: '',
      dataTeams: [
        { appearance_order: 1, team_name: "test1", score: 0 },
        { appearance_order: 2, team_name: "test2", score: 0 },
        { appearance_order: 3, team_name: "test3", score: 0 },
      ],
      nearTeams: [
        { appearance_order: 1, team_name: "", score: 0, image_path: "./img/0.png" },
        { appearance_order: 2, team_name: "", score: 0, image_path: "./img/0.png" },
        { appearance_order: 3, team_name: "", score: 0, image_path: "./img/0.png" },
      ],
      team_image_path: "",
      judges_list: ["judge1", "judge2", "judge3"],
      judge: "",
      if_judge: false

    }
  },
  methods: {
    selectJudge: function(selected_judge){
      this.judge = selected_judge;
      this.if_judge = true
    },
    submitScore: function(team_name, score){
      let index_team = this.dataTeams.findIndex((teams) => {
        return ( teams.team_name=== team_name);
        });
      
      this.dataTeams[index_team].score = score;
    },
    submitAllScore: function(){
      console.log("input_all_score_submit")
    },
    changeScore: function(inputScore){
      console.log("chengeScore", inputScore);
      let nearTeamsList = this.dataTeams
      nearTeamsList.sort((a, b) => {
                if (Math.abs(a.score - inputScore) < Math.abs(b.score - inputScore)) return -1;
                if (Math.abs(a.score - inputScore) < Math.abs(b.score - inputScore)) return 1;
            });
      this.nearTeams = [];
      for(let i = 0; i<3; i++){
        this.nearTeams.push({
          appearance_order: nearTeamsList[i].appearance_order,
          team_name: nearTeamsList[i].team_name,
          score: nearTeamsList[i].score,
          image_path: "./img/" + nearTeamsList[i].appearance_order + ".png"
        })
      }
    },
    input_team: function(){
      console.log("input_team")
    }
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main{
  background-color: #999999;
}
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