<template>
  <div class="home">
    <div class="cards">
      <card-plan
        v-for="card in cards"
        :key="card.index"
        :card="card"
        @cardSelected="changeCardSelected"
      />
    </div>
  </div>
</template>

<script>
import CardPlan from '../components/CardPlan.vue';

export default {
  name: 'Home',
  components: {
    CardPlan,
  },
  data() {
    return {
      cards: [
        {
          index: 0,
          active: false,
          title: { text: 'Guardian', icon: 'skeleton' },
          infos: [
            'Edit up to 10 hours of podcast audio files.',
            'Set your own CoreLoop Page',
          ],
        },
        {
          index: 1,
          active: true,
          price: 480.00,
          title: { text: 'Mage', icon: 'skeleton' },
          infos: [
            'Edit up to 1,000 hours of podcast audio files.',
            'Set your own landing page',
            '24/7 support',
            'Advanced analytics',
          ],
        },
        {
          index: 2,
          active: false,
          price: 600,
          title: { text: 'Phantom', icon: 'skeleton' },
          infos: [
            'Edit up to 4,000 hours of podcast audio files.',
            'Set your own landing page',
            '24/7 support',
            'Advanced analytics',
            'Set sponsor deals',
          ],
        },
      ],
    };
  },
  methods: {
    changeCardSelected(index) {
      this.cards = this.cards.map((card) => {
        const newCard = {
          index: card.index,
          price: card.price,
          title: card.title,
          infos: card.infos,
        };
        if (card.index === index) {
          newCard.active = true;
          return newCard;
        }
        newCard.active = false;
        return newCard;
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.home {
  background-color: $background_home;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  padding-top: 224px;
  .cards {
    display: flex;
    justify-content: space-between;
    background-color: $white;
    border-radius: 20px;
    width: 80%;
  }
}
</style>
