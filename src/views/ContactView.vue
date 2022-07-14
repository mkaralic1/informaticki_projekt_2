<template>
  <div class="contact">
    <v-container>
      <v-row>
        <v-col xs="5" sm="5" md="5" lg="5" xl="5">
          <v-text-field
            v-model="ime"
            label="Ime"
            placeholder="Ovdje unesite svoje ime"
            required
          ></v-text-field>
        </v-col>
        <v-col xs="7" sm="7" md="7" lg="7" xl="7">
          <v-text-field
            v-model="email"
            label="E-mail"
            placeholder="Ovdje unesite svoju e-mail adresu"
            required>
          </v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col xs="5" sm="5" md="5" lg="5" xl="5">
          <v-text-field
           v-model="prezime"
            label="Prezime"
            placeholder="Ovdje unesite svoje prezime"
            required
          ></v-text-field>
        </v-col>
        <v-col xs="7" sm="7" md="7" lg="7" xl="7">
          <v-text-field
            v-model="broj" 
            label="Telefonski broj"
            placeholder="Ovdje unseite svoj telefonski broj(nije obavezno)">
          </v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col xs="12" sm="12" md="12" lg="12" xl="12">
          <v-textarea
          transparent
          v-model='unos'
          name="input-7-4"
          label="Ovdje unesite svoje primjedbe, savjete ili ideje"
          required
        ></v-textarea>
        </v-col>
      </v-row>

      <v-btn @click="podnesi()">
        Podnesi
      </v-btn>
      <v-snackbar
      v-model="snackbar"
      outlined
      >
        {{tekst}}
        <template v-slot:action="{attrs}">
          <v-btn
            color="#fe7c19"
            @click="snackbar=false"
            v-bind="attrs">
          Zatvori
          </v-btn>
        </template>
      </v-snackbar>
    </v-container>
    
  </div>
</template>
<script>
  export default {
    name: "ContactView",
    data: () => ({
      ime: "",
      email: "",
      prezime: "",
      broj: "",
      unos: "",
      snackbar: false,
      tekst: ""
    }),
    methods:{
      podnesi: function(){
        if(this.ime && this.prezime && this.unos && this.email){
          this.tekst="Uspijeh!"
          this.snackbar=true
        }else{
          this.tekst="Nešto nije u redu, pokušaj ponovo."
          this.snackbar=true
        }
      }
    }
  }
</script>