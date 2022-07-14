<template>
  <v-app id="inspire">
    <v-app-bar
      app
      color=#dae416
      flat
    >
      <v-container class="py-0 fill-height">
        <v-row>
          <v-col xs="2" sm="2" md="2" lg="2" xl="2">
            <v-toolbar-title align="left">Pivovare</v-toolbar-title>
            </v-col>
          <v-col><v-btn align="center"
          v-for="[ikona, ruta] in links"
          :key="ikona"
          :to="ruta"
          color="#f5d712"
        >
         {{ikona}}
        </v-btn>
        </v-col>
        </v-row>
        
              
      </v-container>
      
    </v-app-bar>

    <v-main class="white">
      <v-container>
        <router-view></router-view>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
      links: [
        ["Početna", "/"],
        ["Pretraga", "/pretraga"],
        ["Kontakt", "/kontakt"],
        ["O nama", "/about"]
      ],
    }),
  }
</script>
