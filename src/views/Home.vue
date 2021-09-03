<template>
  <div class="home">
    <div class="cards">
      <card-plan
        title="Guardian"
        :infos="[
          'Edit up to 10 hours of podcast audio files.',
          'Set your own CoreLoop Page',
        ]"
      />
      <card-plan
        active
        price="R$ 480,00"
        title="Mage"
        :infos="[
          'Edit up to 1,000 hours of podcast audio files.',
          'Set your own landing page',
          '24/7 support',
          'Advanced analytics',
        ]"
      />
      <card-plan
        price="R$ 600"
        title="Phantom"
        :infos="[
          'Edit up to 4,000 hours of podcast audio files.',
          'Set your own landing page',
          '24/7 support',
          'Advanced analytics',
          'Set sponsor deals',
        ]"
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
};
</script>

<style>
.home {
  background-color: #E5E5E5;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  padding-top: 224px;
}
.cards {
  display: flex;
  justify-content: space-between;
  background-color: #ffffff;
  border-radius: 20px;
  width: 80%;
}
</style>
