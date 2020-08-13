<template>
  <div class="vueMeteo">
      <div class="flex testo-meteo">
          <h5 class="text-center"> {{data.name}} {{data.main.temp}} °</h5>
          <p>{{data.weather[0].description}}</p>
          <!-- <h5 class="text-center">Località XX Gradi</h5>
          <p>Tempo variabile</p> -->
      </div>
      <div class="flex">
           <img class="meteo-icon" :src="data.iconPrefix + data.weather[0].icon + data.iconSuffix" alt="">
           <!-- <img class="meteo-icon" src="http://openweathermap.org/img/wn/04d@2x.png" alt=""> -->
      </div>



  </div>
</template>
<script>
    var prefix= "http://openweathermap.org/img/wn/";
    var suffix ="@2x.png";
export default {
    props: ['data'], // se mi arrivano da un altro componente NON sono DATA ma PROPS
    mounted() {
     // console.log(this.data);
    }

};

// var linkImg = "http://openweathermap.org/img/wn/" + data.weather[0].icon + "@2x.png";
// console.log(linkImg);
</script>

<style lang="scss">
  .vueMeteo {
    display: flex;
    flex-direction: row;
    height: 65px;
    p {
      text-align: center;
      text-transform: capitalize;
    }

    .testo-meteo {
        margin-top: 5px;
    }
    .meteo-icon {
        width: 65px;
    }

  }
</style>
