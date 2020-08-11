<template>
    <div class="vueColFooter">
        <ul>
            <li>{{data.name}}</li>
            <li><a :href="data.github">{{data.github}}</a></li>
            <li> <a :href="data.linkedin">{{data.linkedin}}</a></li>
        </ul>
    </div>
</template>

<script>
    export default {
            props: ["data"]
    };
</script>

<style lang="scss" scoped>
    ul {
        color: red;
    }
    li {
        list-style: none;
    }
</style>
