<template>
  <div class="home">
    <v-row>
      <v-col xs="12" sm="12" md="12" lg="12" xl="12">
        <h2 align="center">
          Došli ste na pravo mjesto, jer ovdje možete pronaći bilo koju pivovaru!
        </h2>
      </v-col>
    </v-row>
    <v-row>
      <v-col xs="1" sm="1" md="2" lg="2" xl="2"></v-col>
      <v-col xs="10" sm="10" md="8" lg="8" xl="8">
        <v-carousel align="center" cycle interval="10000" :show-arrows="false" height="500">
          <v-carousel-item
            v-for="(slika, kljuc) in slike"
            :key="kljuc"
            :src="slika.src"
          >
          </v-carousel-item>
        </v-carousel>
      </v-col>
      <v-col xs="1" sm="1" md="2" lg="2" xl="2"></v-col>
    </v-row>

  
    <v-row>
      <v-col >
        <PivovaraMjeseca
        :ime="pivovara.name"
        :drzava="pivovara.country"
        :grad="pivovara.city"
        ></PivovaraMjeseca>
      </v-col>
    </v-row>    
  </div>
</template>

<script>
import PivovaraMjeseca from "@/components/pivovaraMjeseca.vue"


export default {
  name: 'HomeView',
  components: {
    PivovaraMjeseca
  },
  data(){
    return{
      pivovara: [],
      slike: [
        {
          src: "https://www.sme-news.co.uk/wp-content/uploads/2019/08/Craft-breweries-Brewhouse-Kitchen-Cardiff-Brewery-Bar.jpg"
        },
        {
          src: "https://c1.wallpaperflare.com/preview/259/21/202/brew-copper-boiler-brewery-beer.jpg"
        },
        {
          src: "https://illianabrewbus.com/wp-content/uploads/2018/03/breweries.jpg"
        },
        {
          src: "https://media-cdn.tripadvisor.com/media/photo-s/10/92/60/a1/interior-of-the-micro.jpg"
        }
      ]
    }
  },
  mounted: function(){
    this.axios.get("https://api.openbrewerydb.org/breweries/random")
    .then((response) => {
      this.pivovara=response.data[0]
    })
  }
}
</script>
