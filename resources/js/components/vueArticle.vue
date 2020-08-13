<template>
    <div class="container headlines">
            <div v-if="data.primaPagina == true" class="vueArticle prima-pagina card container">
              <img :src="data.media" alt="">
              <h3 class="text-center"> {{data.title}}</h3>
              <p> {{data.summary}}</p>
              <small> <a :href="data.link">Vai all'articolo completo</a></small>
              <small class="text-center">Fonte: <a :href="data.clean_url"> {{data.rights}} </a></small>
            </div>
            <div v-else class="vueArticle card container">
                <h3 class="text-center"> {{data.title}}</h3>
                <p> {{data.summary}}</p>
                <small> <a :href="data.link">Vai all'articolo completo</a></small>
                <small class="text-center">Fonte: <a :href="data.clean_url"> {{data.rights}} </a></small>
            </div>
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

<style lang="scss">
  h3 {
    font-weight: bold;
    text-transform: lowercase;
  }
  h3::first-letter {
    text-transform: uppercase;
  }

  a {
      text-decoration: none;
      cursor: pointer;
  }

  .vueArticle {
      margin: 10px 0;
  }

  .prima-pagina {
      text-align: center;
      img{
          max-width: 640px;
          object-fit: contain;
          margin: 10px auto;
      }
  }

</style>
