<template>
  <div id="card-container">
    <article>
      <header>
        <h2>{{ this.card.name }}</h2>
        <p>{{ this.card.artist }}</p>
      </header>

      <span class="card-main">
        <img
          :src="getCardImg(this.card.imageUrl)"
          width="376"
          height="522"
          :alt="this.card.title"
        />
      </span>

      <p>{{ this.card.originalText }}</p>
    </article>

    <section>
      <header>
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
header h2 {
  margin-top: 1rem;
}
#card-container {
  background-color: white;
}
article img {
  width: 50%;
}
@media screen and (min-width: 768px) {
  #card-container {
    display: flex;
    justify-content: center !important;
    background-color: white;
  }
  .image {
    display: flex !important;
    text-align: center !important;
    margin: 0 auto !important;
  }
  article img {
    width: 70%;
  }
  section,
  article {
    width: 40%;
  }
  section {
    align-self: center;
  }
}
</style>