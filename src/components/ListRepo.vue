<template>
    <h1>List Repo</h1>
    <ul style="list-style: none">
        <li v-for="depot in depots" :key="depot.id">
            <p>{{ depot.git_url }}</p>
            <p>description: {{depot.description}}</p>
            <a :href="depot.html_url" target="_blank"> Link to the repository</a>
            <p>Created at: {{ depot.created_at}}</p>
            <p>Owner: {{ depot.owner.login}}</p>
        </li>
    </ul>
</template>
<script>
export default {
    props: ['depots']
}
</script>