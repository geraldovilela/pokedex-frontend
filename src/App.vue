<template>
<div>
  <h1>{{titulo}}</h1>
  <ul>
    <li>
      <a v-for="poke of pokedata" v-bind:href="poke.url">
      <img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1.png"></img>
       {{poke.name}}
      </a>
    </li>
  </ul>
    <button><a :href="previous" >Previous</a></button>
    <button><a :href="next" >Next</a></button>
</div>
</template>

<script>
export default {
  data() {
    return {
      titulo: "PokeList",
        next:"",
        previous:"",
        pokedata:[
        ]
    }
  },
  created(){
      this.$http.get("https://pokeapi.co/api/v2/pokemon/")
        .then(res => {
          res.json()
          .then(data =>{
              this.pokedata = data.results;
              this.next = data.next;
              this.previous = data.previous;
          }, err=>console.log(err));
        })



    }
}
</script>

<style lang="scss">

</style>
