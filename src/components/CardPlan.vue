<template>
  <div
    class="card"
    :class="cardActiveClass"
  >
    <div class="info">
      <h1>
        <img
          v-if="active"
          src="../assets/skeleton-white.svg"
        >
        <img
          v-else
          src="../assets/skeleton.svg"
        >
        {{ title }}
      </h1>
      <p>{{ subtitle }}</p>
      <div :class="checksClass">
        <div
          v-for="(item, index) in infos"
          :key="index"
        >
          <img
            v-if="active"
            src="../assets/check-white.svg"
          >
          <img
            v-else
            src="../assets/check.svg"
          >
          <span>{{ item }}</span>
        </div>
      </div>
    </div>
    <div class="card-footer">
      <h1 class="price">
        {{ price }}
      </h1>
      <button :class="chooseButtonClass">
        Choose
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardPlan',
  props: {
    active: {
      type: Boolean,
      default: false,
    },
    price: {
      type: String,
      default: 'Free Forever',
    },
    title: {
      type: String,
      default: '',
    },
    subtitle: {
      type: String,
      default: 'What You’ll Get',
    },
    infos: {
      type: Array,
      default: () => [],
    },
  },
  computed: {
    cardActiveClass() {
      return this.active ? 'selected' : '';
    },
    checksClass() {
      return this.active ? 'checks-selected' : 'checks';
    },
    chooseButtonClass() {
      return this.active ? 'choose-button-active' : 'choose-button';
    },
  },
};
</script>

<style>
.card {
  max-width: 400px;
  background-color: #ffffff;
  margin: 10px;
  border-radius: 20px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.selected {
  background-color: #0B0641;
  transform: translateY(-40px);
  color: #ffffff;
}

.card > .info > h1 {
  display: flex;
  margin-bottom: 32px;
}

.card > .info > p {
  color: #A9A9AA;
  font-size: 22px;
}

.card > .info > h1 > img {
  margin-right: 20px;
}

.card > .info > .checks-selected {
  border-bottom: 1px dashed #ffffff;
  padding: 10px 0px;
}

.card > .info > .checks {
  border-bottom: 1px dashed #A9A9AA;
;
  padding: 10px 0px;
}

.card > .info > .checks div,
.card > .info > .checks-selected div {
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  margin: 24px 0px;
}

.card > .info > .checks div span,
.card > .info > .checks-selected div span {
  font-size: 18px;
  margin-left: 6px;
}

.card > .card-footer {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card > .card-footer > .price {
  width: 100%;
  text-align: left;
  margin-top: 64px;
  margin-bottom: 24px;
}

.card > .card-footer > .choose-button-active,
.card > .card-footer > .choose-button {
  width: 100%;
  padding: 20px;
  border-radius: 12px;
  border: none;
  font-size: 22px;
  line-height: 40px;
}

.card > .card-footer > .choose-button-active {
  background: #ff1d89;
  box-shadow: 0px 12px 32px rgba(255, 29, 137, 0.5);
  color: #ffffff;
  font-weight: 600;
}

.card > .card-footer > .choose-button {
  background: #FFF5FA;
  color: #ff1d89;
  font-weight: 600;
}
</style>
