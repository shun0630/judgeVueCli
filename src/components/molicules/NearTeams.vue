<template>
    <h2>全チームリスト</h2>
    <table>
        <thead>
            <tr>
                <td>出演順</td>
                <td>チーム名</td>
                <td>得点</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="team in near-teams-list" :key="team.appearance_order">
                <td>{{ team.appearance_order }}</td>
                <td>{{ team.team_name }}</td>
                <td>{{ team.score }}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    name: "NearTeams",
    props:["near-teams-list"]

};
</script>