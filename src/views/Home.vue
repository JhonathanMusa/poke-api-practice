<template>
  <div>
    <v-container>
      <v-row no-gutters style="height: 150px">
        <v-col xs="12">
          <v-card class="mx-auto my-12" max-width="400">
            <v-img
              height="250"
              max-height="150"
              max-width="400"
              src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/1200px-International_Pok%C3%A9mon_logo.svg.png"
            >
            </v-img>
            <v-card-title class="text-center"
              >Pokemon # 
              <template>
                <v-text-field
                  v-model="number"
                  @keyup.enter="search"
                  color="warning"
                  loading
                ></v-text-field>
                <v-btn @click="search" block color="secondary">Search</v-btn>
              </template>
            </v-card-title>
            <v-divider class="mx-4"></v-divider>
            <!-- <v-card-text v-for="pokemon in pokemonName" v-bind:key="pokemon.id">
              {{pokemon}}
            </v-card-text> -->
            <v-card-text class="text-center headline">
              {{ pokemonName }}
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      number: null,
      pokemonName: "",
    };
  },
  methods: {
    async getPokemon(num) {
      try {
        // let res = await axios.get(`https://pokeapi.co/api/v2/pokemon/`);
        let res = await axios.get(`https://pokeapi.co/api/v2/pokemon/?offset=0&limit=151`);
        // console.log(res.data.results[num].name);
        this.pokemonName = res.data.results[num].name;
      } catch (error) {
        console.log(error);
      }
    },
    search() {
      this.getPokemon(this.number);
    },
  },
};
</script>
