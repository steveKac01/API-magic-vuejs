<template>
    <article>
        <header class="major">
            <h2>Ma Collection</h2>
        </header>
        <div class='card-list' v-for="card in this.cards" :key="card.id">
            <div class='card-title'><b>#tt {{cardCount()}} - </b>{{card.name}}</div>
            <div class='card-action' @click="goToCardDetail(card.id)">👀</div>
        </div>
      
    </article>
</template>




<script>
import axios from "axios";

export default {
  data: () => ({
    cards: {},
    iCard:0
  }),
methods:{
    goToCardDetail(id){
        this.$router.push({name:"card",params:{id}})
    }
    ,
    cardCount()
    {    
        return  this.iCard++;  //Note pour rémi: je ne comprends pas, il démarre à # 10001
    }
},  async created() {
let temp = await axios.get("https://api.magicthegathering.io/v1/cards");
this.cards = temp.data.cards;
console.log(this.cards)
  }

}
</script>

<style>
@import url("../assets/style/card-list.css");
.card-action{
    cursor: pointer;
}
</style>