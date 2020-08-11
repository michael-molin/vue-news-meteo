<template>
  <div class="vueArticle card container">
    <h3 class="text-center"> {{data.title}}</h3>
    <p> {{data.summary}}</p>
    <small> <a :href="data.link">Vai all'articolo completo</a></small>
    <small class="text-center">Fonte: <a :href="data.clean_url"> {{data.rights}} </a></small>
  </div>
</template>
<script>
export default {
    props: ['data'], // se mi arrivano da un altro componente NON sono DATA ma PROPS
  mounted() {
  //  console.log(this.data);
  }
};
</script>

<style media="SCSS">
  h3 {
    font-weight: bold;
    text-transform: lowercase;

  }
  h3::first-letter {
    text-transform: uppercase;
  }
</style>
