 <template>
  <div id="main-wrapper">
    <div class="wrapper style1">
      <div class="inner">
        <!-- Feature 1 -->
        <section class="container box feature1">
          <div class="row">
            <div class="col-12">
              <header class="first major">
                <h2>Mes 3 Dernières Cartes</h2>
              </header>
            </div>
            <div
              class="col-4 col-12-medium"
              v-for="card in this.cards"
              :key="card.id"
            >
              <section>
                <img
                  :src="getCardImg(card.imageUrl)"
                  alt=""
                  width="203"
                  height="310"
                  @click="goToCardDetail(card.id)"
                />
                <header class="second icon solid fa-dragon">
                  <h3>{{ card.name }}</h3>
                  <p>{{ card.type }}</p>
                </header>
              </section>
            </div>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>
 
 
<script>
import axios from "axios";

export default {
  data: () => ({
    cards: {},
    numberOfCard: 3,
  }),
  async created() {
    let temp = await axios.get(
      "https://api.magicthegathering.io/v1/cards?pageSize=3"
    );
    this.cards = temp.data.cards;
  },
  methods: {
    goToCardDetail(id) {
      this.$router.push({ name: "card", params: { id } });
    },
    getCardImg(url) {
      if (url != null) {
        return url;
      } else {
        return "https://via.placeholder.com/203x310?text=No+Img+Found";
      }
    },
  },
};
</script>

<style scoped>
img {
  cursor: pointer;
}
</style>