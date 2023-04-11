<template>
  <div class="home" style="background-image: url(https://images3.alphacoders.com/812/812062.png);">
    <div v-if="online()">
    <h1 style="color: white;">Rick and Morty</h1>
    <div class="container" >
      <div v-for="(character, index) in characters" :key="index">
    <mat-card class="card" style="width: 18rem;">
            <h3>{{ character.name }}</h3>
          <div>{{ character.gender }}</div>
        <div>{{ character.status }}</div>
            <img :src="character.image" alt="">  
          </mat-card>
        </div>
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
      characters: null,
      isMounted: false,
    };

  },
  
  methods: {
    online(){
      return window.navigator.onLine;
    },
 },
async mounted(){
  await axios.get('https://rickandmortyapi.com/api/character/')
      .then(res => {
        (this.characters = res.data.results)
      })
      .catch(e => {
        console.log(e)
      })
      this.isMounted = true;
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
