<template>
  <v-container>
    <h1 align="center">Pivovara mjeseca</h1>
    <br>
    <v-card
    class="mx-auto"
    max-width="344"
  >
    <v-card-text>
      <p class="text-h4 text--primary">
        {{ime}}
      </p>
      <v-row>
        <v-col>Država</v-col>
        <v-col>{{drzava}}</v-col>
      </v-row>
      <v-row>
        <v-col>Grad</v-col>
        <v-col>{{grad}}</v-col>
      </v-row>
    </v-card-text>
  </v-card>
  </v-container>
</template>

<script>
  export default{
    name: "pivovaraMjeseca",
    props: ["ime", "drzava", "grad"],
    data: ()=>({})
  }
</script>