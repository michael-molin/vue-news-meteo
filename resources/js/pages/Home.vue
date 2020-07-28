<template>
    <div class="container">
        <vueHeader> </vueHeader>
        <vueMain> </vueMain>
        <vueFooter> </vueFooter>
    </div>

</template>
<script>                                                                        // Script init vue
    import vueHeader from "../components/vueHeader";                                  // importo il componente header usando il path
    import vueMain from "../components/vueMain";                                  // importo il componente header usando il path
    import vueFooter from "../components/vueFooter";                                  // importo il componente header usando il path
    export default {                                                            // struttura per inserire i file nei componenti
        components: {
            vueHeader,
            vueMain,
            vueFooter
        },
        mounted() {
        //     const axios = require("axios");
        //
        //     axios({
        // "method":"GET",
        // "url":"https://community-open-weather-map.p.rapidapi.com/weather",
        // "headers":{
        // "content-type":"application/octet-stream",
        // "x-rapidapi-host":"community-open-weather-map.p.rapidapi.com",
        // "x-rapidapi-key":"a7dd0fdc79msh2fc535c6135eb9cp1dad9ajsn8f651fcf8a2b",
        // "useQueryString":true
        // },"params":{
        // "callback":"test",
        // "id":"2172797",
        // "units":"metric",
        // "mode":"html",
        // "q":"London%2Cuk"
        // }
        // })
        // .then((response)=>{
        //   console.log(response)
        // })
        // .catch((error)=>{
        //   console.log(error)
        // })
    }
};
</script>
<style lenght="scss" scoped>
    .container {
        width: 100vw;
    }
</style>
