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
            <tr  v-for="item in items" :key="item.appearance_order">
                <td>{{ item.appearance_order }}</td>
                <td>{{ item.team_name }}</td>
                <td>{{ item.score }}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    name: "TeamTable",
    props: ["items"]
}
</script>

<style>
table, th, td{
    border-collapse: collapse;
    border: 1px solid #ccc;
    text-align: center;
    margin: auto;
}
</style>