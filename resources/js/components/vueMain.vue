<template>

    <div class="container">
        <vueArticle></vueArticle>
    </div>

</template>
<script>
    import vueArticle from "../components/vueArticle";
    export default {                                                            // struttura per inserire i file nei componenti
        components: {
            vueArticle
        },
        data() {
            return {
                dati: []
                }
            },
        mounted() {
            var self = this; // = al THEN
            return axios('http://newsapi.org/v2/top-headlines?country=it&apiKey=e81f993c9f994236ae8ea437aa2b1cd9', {
             method: 'GET',
             mode: 'no-cors',
             headers: {
               // 'Access-Control-Allow-Origin': null,
               'Content-Type': 'application/json',
             },
             withCredentials: false,
             credentials: 'same-origin',
            }).then(response => {
            })
        }
    }
</script>
