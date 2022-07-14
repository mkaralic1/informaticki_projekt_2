<template>
  <v-container>
    <v-card
    class="mx-auto"
    max-width="344"
  >
    <v-card-text>
      <p class="text-h6 text--primary">
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
      <v-row>
        <v-col>
          <a :href=web target="_blank">WEB stranica</a>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
  </v-container>
</template>

<script>
  export default{
    name: "vidiPivovaru",
    props: ["ime", "drzava", "grad", "web"],
    data: ()=>({})
  }
</script>