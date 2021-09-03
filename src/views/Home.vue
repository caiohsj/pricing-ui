<template>
  <div class="home">
    <div class="cards">
      <card-plan />
      <card-plan active />
      <card-plan />
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
}
.cards {
  display: flex;
  justify-content: space-between;
  background-color: #ffffff;
  border-radius: 20px;
  height: 80%;
  width: 80%;
}
</style>
