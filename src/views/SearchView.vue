<template>
  <div class="search">
    <v-container>
    <h1 align="center">Pronađi pivovaru</h1>
    <v-row>
      <v-col xs="2" sm="2" md="2" lg="2" xl="2">
        <v-menu>
          <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          {{ime}}
        </v-btn>
      </template>
          <v-list>
            <v-list-item
            v-for="(kategorija, index) in kategorije"
            :key="index"
            >
              <v-list-item-title
              @click="promjeni(kategorija.naslov, kategorija.vrijednost)"
              >
                {{kategorija.naslov}}
              </v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </v-col>
      <v-col xs="10" sm="10" md="10" lg="10" xl="10">
        <v-text-field color=black large label="Pretraga"
        v-model="pretraga" 
        @keydown.enter="novaPretraga()">
        </v-text-field>
      </v-col>
    </v-row>
    <v-container>
      <v-row>
      <v-col xs="12" sm="6" md="4" lg="4" xl="4"
      v-for="pivovara in pivovare" :key="pivovara.id"
      >
        <vidi-pivovaru
        :ime="pivovara.name"
        :drzava="pivovara.country"
        :grad="pivovara.city"
        :web="pivovara.website_url"
        >
        </vidi-pivovaru>
      </v-col>
    </v-row>
    </v-container>
    
    </v-container>  
    <v-row>
      <v-col cols="12">
        <v-pagination
        v-if="result"
        @input="dohvatiApi()"
        v-model="stranica"
        :length="10"
        >
        </v-pagination>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import vidiPivovaru from '@/components/vidiPivovaru.vue'

export default {
  components: { vidiPivovaru },
  name: 'SearchView',
  data:() => ({
    pretraga: "",
    pretraga1: "",
    stranica: 1,
    pivovare: [],
    result: false,
    kategorije: [
      {naslov: "Ime", vrijednost: "by_name="},
      {naslov: "Država", vrijednost: "by_country="},
      {naslov: "Grad", vrijednost: "by_city="}      
    ],
    ime: "Kategorije",
    broj: 1,
  }),
  methods:{
    novaPretraga: function(){
      this.dohvatiApi()
      this.stranica=1
    },
    
    dohvatiApi: function(){
      this.axios.get("https://api.openbrewerydb.org/breweries?"+this.pretraga1+this.pretraga+"&per_page=12&page="+this.stranica)
      .then(response => {
        this.pivovare=response.data
        this.result=true
        this.broj=this.pivovare.length
      })
    },
    promjeni: function(ime, value){
      this.ime=ime
      this.pretraga1=value
    }
  }
}
</script>
