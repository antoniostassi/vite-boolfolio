<script>
import axios from 'axios';

export default {
  data() {
    return {
      pokemons: [],
    }
  },
  mounted(){
    this.getPokemonsData();
  },
  methods:{
    getPokemonsData(){
      axios.get('http://127.0.0.1:8000/api/pokemon')
          .then((res)=>{
            this.pokemons = res.data.data
          })
    }
  }
}
</script>

<template>
  <main>
    <div class="container">
      <div class="row">
          <div class="col">
            <table class="table table-striped table-hover">
              <thead>
                <tr>
                  <th scope="col">ID</th>
                  <th scope="col">Pokemon</th>
                  <th scope="col">Tipo</th>
                  <th scope="col">Azioni</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="pokemon in pokemons">
                  <th scope="row">{{ pokemon.id }}</th>
                  <td class="text-capitalize">{{pokemon.name}}</td>
                  <td>
                    <span v-for="type in pokemon.types"
                     class="badge text-capitalize bg-secondary-subtle me-2"
                     :style="{color:type.color}">
                      {{type.name}}
                    </span>
                  </td>
                  <td>
                    <router-link :to="{name:'show', params:{id: pokemon.id}}" class="btn btn-primary btn-sm">
                      Visualizza info Pokemon
                    </router-link>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables' as *;
main{
  height:70vh;
}

</style>