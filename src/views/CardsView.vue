<template>
  <article>
    <header class="major">
      <h2>Ma Collection</h2>
    </header>
    <div class="card-list" v-for="(card, id) in this.cards" :key="id">
      <div class="card-title">
        <b>#{{ id + 1 }} - </b>{{ card.name }}
      </div>
      <div class="card-action" @click="goToCardDetail(card.id)">👀</div>
    </div>
  </article>
</template>

<script>
import axios from "axios";

export default {
  data: () => ({
    cards: {},
    iCard: 0,
  }),
  methods: {
    goToCardDetail(id) {
      this.$router.push({ name: "card", params: { id } });
    },
  },
  async created() {
    let apiResult = await axios.get(
      "https://api.magicthegathering.io/v1/cards"
    );
    this.cards = apiResult.data.cards;
  },
};
</script>

<style>
@import url("../assets/style/card-list.css");
.card-action {
  cursor: pointer;
}
</style>