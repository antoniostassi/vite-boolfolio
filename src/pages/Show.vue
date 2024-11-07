<script>
import AppHeader from '../components/AppHeader.vue';
import AppFooter from '../components/AppFooter.vue';
import axios from 'axios';
export default {
  data() {
    return{
        pokemon:'',
        generation:''
    }   
  },
  components: {
    AppHeader,
    AppFooter
  },
  mounted(){
    this.getPokemonData();
  },
  methods:{
    getPokemonData(){
      axios.get('http://127.0.0.1:8000/api/pokemon/'+ this.$route.params.id)
          .then((res)=>{
            this.pokemon = res.data.pokemon;
            this.generation = res.data.pokemon.generation.name;

            
          })
          .catch((err)=>{
            console.error(err);
            this.$router.push({
                name: 'not-found'
            })
          })
    }
  }
}
</script>


<template>
    <AppHeader />
    <div class="container">
        <div class="row">
            <div class="col-12">
                <div class="card">
                    <div class="card-body">
                        <h5 class="card-title text-capitalize">{{ pokemon.name }}</h5>
                        <p class="card-text">{{pokemon.description}}</p>
                        <p class="card-text">Peso: {{pokemon.weight}} KG</p>
                        <p class="card-text">Altezza: {{pokemon.height}} CM</p>
                        <p v-if="pokemon.sex != 'U'" class="card-text">{{ pokemon.sex == 'M' ? 'Sesso: Maschio' : 'Sesso: Femmina' }}</p>
                        <p v-else>Sesso: Indefinito</p>

                        <p class="card-text">
                            
                            <span v-for="type in pokemon.types"
                                class="badge text-capitalize bg-secondary-subtle me-2"
                                :style="{color:type.color}">
                                {{type['name']}}
                            </span>
                            
                        </p>
                        <p class="card-text">Generazione: {{generation}}</p>
                    </div>
                    <img :src="'http://localhost:8000/storage/' + pokemon.picture" class="card-img-bottom" :alt="pokemon.name">
                </div>
            </div>
        </div>
    </div>
    <AppFooter />
</template>
  
<style lang="scss" scoped>

</style>