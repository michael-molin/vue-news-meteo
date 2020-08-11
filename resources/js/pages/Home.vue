<template>
    <div class="container">
        <vueHeader> </vueHeader>
        <vueMain> </vueMain>
        <vueFooter> </vueFooter>
    </div>

</template>
<script>                                                                        // Script init vue
    import Vue from 'vue';
    import "font-awesome/css/font-awesome.min.css";
    Vue.component('VueFontawesome', require('vue-fontawesome-icon/VueFontawesome.vue').default);

    import vueHeader from "../components/vueHeader";                                  // importo il componente header usando il path
    import vueMain from "../components/vueMain";                                  // importo il componente header usando il path
    import vueFooter from "../components/vueFooter";                                  // importo il componente header usando il path
    export default {                                                            // struttura per inserire i file nei componenti
        components: {
            vueHeader,
            vueMain,
            vueFooter
        }
};
</script>
<style leng="scss" scoped>
    .container {
        width: 100vw;
    }
</style>
