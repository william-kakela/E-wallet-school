<template>
  <div>
    <Top title="E-wallet" />
    <Card
      :number="card.number"
      :holder="card.holder"
      :valid="card.valid"
      :vendor="card.vendor"
    />

    <div class="remove-btn-wrapper" v-if="card.holder.length > 0">
      <button @click="removeCard" class="remove-btn">Remove card</button>
    </div>

    <CardStack @selectCard="selectCard" :cards="cards" />

    <router-link to="/add_card" id="add-card"> Add a new card </router-link>
  </div>
</template>

<script>
import Top from "@/components/Top";
import Card from "@/components/Card";
import CardStack from "@/components/CardStack";

export default {
  name: "Home",
  components: {
    Top,
    Card,
    CardStack,
  },

  created() {
    if (!localStorage.getItem("cards")) {
      this.cards = [
        {
          number: "123412341234",
          holder: "William Käkelä",
          valid: "18/23",
          ccv: "111",
          vendor: "ninja_corp",
        },
        {
          number: "234523452345",
          holder: "William Käkelä",
          valid: "17/22",
          ccv: "222",
          vendor: "block_chain",
        },
        {
          number: "345634563456",
          holder: "William Käkelä",
          valid: "08/22",
          ccv: "333",
          vendor: "evil_corp",
        },
      ];
      const jsonCards = JSON.stringify(this.cards);
      localStorage.setItem("cards", jsonCards);
    } else {
      const jsonCards = localStorage.getItem("cards");
      this.cards = JSON.parse(jsonCards);
    }
  },
  data() {
    return {
      cards: [],
      card: {
        number: "",
        holder: "",
        vendor: "",
        ccv: "",
        valid: "",
        index: 0,
      },
    };
  },
  methods: {
    selectCard(card, index) {
      this.card = card;
      this.card.index = index;
    },
    removeCard() {
      this.cards.splice(this.card.index, 1);

      this.card = {
        number: "",
        holder: "",
        vendor: "",
        ccv: "",
        valid: "",
      };
      const lessCards = JSON.stringify(this.cards);
      localStorage.setItem("cards", lessCards);
    },
  },
};
</script>

<style scoped>
.remove-btn-wrapper {
  padding: 0 1rem;
}
#add-card {
  display: block;
  text-align: center;
  border-radius: 5px;
  padding: 1rem;
  text-transform: uppercase;
  border: 1px solid black;
  margin: 0 1rem;
  text-decoration: none;
  color: #000000;
}

.remove-btn {
  width: 100%;
  background-color: #ffffff;
  border-radius: 5px;
  margin-top: 1rem;
  border: 1px solid black;
  padding: 1rem 0;
}
</style>
