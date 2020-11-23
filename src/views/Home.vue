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
              >Pokemon - 
              <template>
                <v-text-field v-model="number" @keyup.enter="search"></v-text-field>
                <v-btn @click="search" block color="secondary">Search</v-btn>
              </template>
            </v-card-title>
            <v-divider class="mx-4"></v-divider>
            <v-card-text>
              {{number}}
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
      pokemonName: [],
    };
  },
  methods: {
    async getPokemon(num) {
      try {
        let data = await axios.get(`https://pokeapi.co/api/v2/pokemon/`);
        console.log(data.data.results[num]);
      } catch (error) {
        console.log(error);
      }
    },
    search() {
      console.log(this.getPokemon(this.number));
    },
  },
};
</script>
