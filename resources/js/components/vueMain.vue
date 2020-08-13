<template>
    <div>
        <div class="full-width">
            <div class="container barra-flex">
                <vueSearch class="search" @clicked="onClickChild" @keypress.13="onClickChild"></vueSearch>
                <vueMeteo class="meteo" v-model="dataMeteo" :data="dataMeteo"></vueMeteo>
            </div>
        </div>
        <vueArticle v-for="(article, index) in articles" :key="index" :data="article"></vueArticle>
    </div>

</template>

<script>
    import vueArticle from "../components/vueArticle";
    import vueSearch from "../components/vueSearch";
    import vueMeteo from "../components/vueMeteo";
    export default { // struttura per inserire i file nei componenti
        components: {
            vueArticle,
            vueSearch,
            vueMeteo
        },
        data() {
            return {
                articles: [],
                dataMeteo: {}
            }
        },
        mounted() {
            const axios = require("axios");
            var self = this;
            var http = require('http');


            http.get({'host': 'api.ipify.org', 'port': 80, 'path': '/'}, function(resp) {
                resp.on('data', function(ip) {
                    var myActualIp = ip.toString();
                    console.log(myActualIp); // STAMPO IP

                    var api_key = 'at_eIgLTrnumViPHcllCfsgy0qUTAlir';
                    var api_url = 'https://geo.ipify.org/api/v1?';

                    var urlCompleto = api_url + 'apiKey=' + api_key + '&ipAddress=' + myActualIp;
                    http.get(urlCompleto, function(response) {
                        var str = '';
                        response.on('data', function(chunk) { str += chunk; }); // PUSHA i CHUNK DENTRO STR
                        response.on('end', function() {
                          var localizzazione = JSON.parse(str); // trasformo la stringa in OGGETTO
                          var localita = localizzazione.location.city;
                          // CHIAMATA CHE PRENDE LA LOCALITA DALL IP E RESTITUISCE METEO
                          axios({
                              "method": "GET",
                              "url": "https://community-open-weather-map.p.rapidapi.com/weather",
                              "headers": {
                                  "content-type": "application/octet-stream",
                                  "x-rapidapi-host": "community-open-weather-map.p.rapidapi.com",
                                  "x-rapidapi-key": "c8b7cc50c3msh9fe9e3f2a455018p1ec642jsnbd51f6bc37d2",
                                  "useQueryString": true,
                                  'Access-Control-Allow-Headers': 'application/json'
                              },
                              "params": {
                                  "units": "Metric",
                                  "lang": 'it',
                                  "q": localita

                              },
                              contentType: 'application/json',
                              dataType: "jsonp",
                              responseType: 'application/json'
                          }).then((response) => { // LA RISPOSTA DALL API
                              console.log(response.data);
                              response.data.iconPrefix = "http://openweathermap.org/img/wn/"; // AGGIUNGO PREFIX
                              response.data.iconSuffix= "@2x.png" // AGGIUNGO SUFFIX
                              self.dataMeteo = response.data;

                          }).catch((error) => {
                              console.log(error);
                          })
                      });
                    }).end();
                });
            });


            // CHIAMATA CHE RESTITUISCE ARTICOLI
            axios({
                "method": "GET",
                "url": "https://newscatcher.p.rapidapi.com/v1/latest_headlines",
                "headers": {
                    "content-type": "application/octet-stream",
                    "x-rapidapi-host": "newscatcher.p.rapidapi.com",
                    "x-rapidapi-key": "a7dd0fdc79msh2fc535c6135eb9cp1dad9ajsn8f651fcf8a2b",
                    "useQueryString": true
                },
                "params": {
                    "lang": "it",
                    "media": "True"
                }
            }).then((response) => {
                var rawArticles = response.data.articles;
                var primaPagina = false;
                for (var index in rawArticles) {
                    var article = rawArticles[index];
                    if (article.media != null && primaPagina == false) {
                        primaPagina = true;
                        article.primaPagina= true;
                        self.articles.unshift(article);
                    } else {
                        article.primaPagina= false;
                        self.articles.push(article);
                    }
                }
            }).catch((error) => {
                console.log(error)
            });


        },


        computed: {},
        methods: {
            onClickChild(value) {
                const axios = require("axios"); // CHIAMATA PER NUOVI ARTICOLI DA CERCARE
                var self = this;
                var valore = value;
                axios({
                    "method":"GET",
                    "url":"https://newscatcher.p.rapidapi.com/v1/search_free",
                    "headers":{
                        "content-type":"application/octet-stream",
                        "x-rapidapi-host":"newscatcher.p.rapidapi.com",
                        "x-rapidapi-key":"a7dd0fdc79msh2fc535c6135eb9cp1dad9ajsn8f651fcf8a2b",
                        "useQueryString":true
                    },
                    "params":{
                        "media":"True",
                        "lang":"it",
                        "q":valore
                    }
    })
    .then((response)=>{
        self.articles= response.data.articles;
    })
    .catch((error)=>{
        console.log(error);
    })

            }
        }
    }
</script>

<style lang="scss">


    .full-width {
        background-color: #41b883;
        .barra-flex {
            display: flex;
            flex-direction: row;
            justify-content: space-between;
            align-items: center;
        }

    }
</style>
