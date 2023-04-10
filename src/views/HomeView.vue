<template>
  <div class="home" style="background-image: url(https://images3.alphacoders.com/812/812062.png);">
    <h1 style="color: white;">Rick and Morty</h1>
    <div class="container" >
      <div v-for="(character, index) in characters" :key="index">
    <mat-card class="card" style="width: 18rem;">
      <!-- <mat-card-header> -->
            <h3>{{ character.name }}</h3>
          <div>{{ character.gender }}</div>
        <div>{{ character.status }}</div>
            <img :src="character.image" alt="">
            <!-- </mat-card-header> -->
          </mat-card>
        </div>
        </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';

export default {
  name: 'HomeView',
  components: {
  },
  data(){
    return{
      characters: null
    }

  },
  mounted(){
    console.log('verificando')
    this.getTodos();
  },
  methods: {
    getTodos(){
        axios.get('https://rickandmortyapi.com/api/character/')
      .then(res => {
        (this.characters = res.data.results)
      })
      .catch(e => {
        console.log(e)
      })
  }
 }
}
</script>

<style>
body{
  margin: 0px;
  margin-top: 0px;
  /* background-color:black ; */
}
.card{
    margin: 3rem;
    width: 200px;
    height: 200px;
    color: white;
    /* margin-top: 28rem; */
}

.container{
    align-content: center;
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    justify-content: center;

    
}
</style>
