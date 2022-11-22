<template>
  <div class="row">
    <div class="col-8 col-12-medium">
      <div id="content">
        <!-- Content -->

        <article>
          <header class="major">
            <h2>{{ this.card.name }}</h2>
            <p>{{ this.card.artist }}</p>
          </header>

          <span class="image featured">
            <img
              :src="getCardImg(this.card.imageUrl)"
              width="376"
              height="522"
              :alt="this.card.title"
            />
          </span>

          <p>{{ this.card.originalText }}</p>
        </article>
      </div>
    </div>
    <div class="col-4 col-12-medium">
      <div id="sidebar">
        <!-- Sidebar -->

        <section>
          <header class="major">
            <h2>Infos</h2>
          </header>
          <p>
            set name: <b>{{ this.card.setName }}</b>
          </p>
          <p>
            rarity: <b>{{ this.card.rarity }}</b>
          </p>
          <p>
            toughness: <b>{{ this.card.toughness }}</b>
          </p>

          <span class="button alt icon">
            Card power
            <i class="fa-solid fa-fire-flame-curved">{{ getPower() }}</i>
          </span>
        </section>
      </div>
    </div>
  </div>
</template>




<script>
import axios from "axios";

export default {
  async created() {
    let apiResult = await axios.get(
      "https://api.magicthegathering.io/v1/cards/" + this.$route.params.id
    );
    this.card = apiResult.data.card;
  },
  data: () => ({
    card: {},
  }),
  methods: {
    /**
     * Get the power of the card using emoji.
     */
    getPower() {
      return "🔥".repeat(this.card.power);
    },
    /**
     * Get the img of the card if the api provide an URL, if not returns a placeholder.
     */
    getCardImg(url) {
      if (url != null) {
        return url;
      }
      
      return "https://via.placeholder.com/376x522?text=Loading+Image";
    },
  },
};
</script>

<style scoped>
img {
  width: 30%;
}
</style>