<template>
<div class="body">
  <h1 class="header">{{titulo}}</h1>
  <ul class="content">
    <li>
    <div class="inner-content">
      <div class="item" v-for="poke of pokedata" v-bind:href="poke.id">
      <img :src="poke.frontMale"></img>
       {{poke.name}}
      </div>
    </div>
    </li>
  </ul>

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
      this.$http.get("https://localhost:44336/api/Pokemons")
        .then(res => {
          res.json()
          .then(data =>{
            this.pokedata = data;
          }, err=>console.log(err));
        })



    }
}
</script>

<style lang="scss">
  .body {
    width:90%;
    font-family:Helvetica, sans-serif;
    margin: 0 auto;
    align-self:center;
    background:rgb(15,255,150);
  }

  .header{
    text-align:center;
  }

  .content {
    list-style:none;
  }

  .inner-content {
    display:flex;
    align-content: space-between;
    justify-content: space-evenly;
  }

  .item {
    display:flex;
    flex-direction:column;
  }
</style>
