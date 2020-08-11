<template>

<div class="col-12">
    <vueColFooter v-for="(dato, index) in dati" :key="index" :data="dato" class="col-6">
    </vueColFooter>
</div>

</template>


<style lang="scss" scoped>
    .vueColFooter {
        display: inline-block;
    }
</style>
<script>
    import vueColFooter from "../components/vueColFooter";
    export default {                                                            // struttura per inserire i file nei componenti
        components: {
            vueColFooter
        },
        data() {
            return {
                dati: [{
                        name: "Mirko",
                        github: "Link Github",
                        linkedin: "link Linkedin"
                    },
                    {
                        name: "Michael",
                        github: "Link Github",
                        linkedin: "link Linkedin"
                    }]
                }
            }
        }
</script>
