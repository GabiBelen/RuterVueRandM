<template>
  <div class="container mt-5">
    <h2 class="fst-italic text-center mb-5">Lista de Personajes</h2>

    <div class="row" v-for="character of characters" :key="character.id">
      <div class="col">
        <h3>{{ id.title.charAt(0).toUpperCase() + id.title.slice(1) }}</h3>
        <!-- PERSOJNAJES -->
        <router-link class="personaje" :to="`${character.userId}`">Personaje</router-link>
        <p>{{ character.body }}</p>
        <button class="btn btn-secondary" @click="id(character.id)">Ver datos</button>

        <template v-for="characterFiltrado of charactersFiltrados" :key="characterFiltrado.id"> 
          <div class="mt-3 col-sm-10 offset-sm-1" v-if="characterFiltrado.postId ===  character.id">
            <p class="mt-4 fw-bold"> User: {{ characterFiltrado.email}}</p>
            <br>
            <p> Caracteristicas: </p>
            <p>{{ characterFiltrado.body}}</p>
          </div>
        </template>
        <hr/>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'HomeView',
  components: {
  },
  data() {
    return {
      characters: [],
      charactersFiltrados: []
    }
  },
  methods: {
    comentariosid(id){
      // console.log(id); esto es id posts
      this.charactersFiltrados = this.characters.filter( character => character.charactersId == id);
      console.log(this.charactersFiltrados);
    },
    async consumirCharacters() {
      try {
        const data = await fetch(`https://rickandmortyapi.com/api/character`);
        const getcharacter = await data.json();
        this.character = get.characters;
        console.log(this.characters)
      } catch (error) {
        console.log(error);
        throw error;
      }
    }
  },
  created() {
    this.consumirCharacters();
  }
}
</script>

<style scoped>
 h3 {
   font-size: 16px !important;
 }
 a {
   text-decoration: none;
   color: #544e4e;
   background:bisque;
   padding: 2px 7px;
   border-radius: 5px;
 }
</style>