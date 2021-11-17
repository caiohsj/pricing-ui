<template>
  <div
    class="card"
    :class="cardActiveClass"
    @click="clickedCard"
  >
    <div class="info">
      <h1>
        <img
          v-if="card.active"
          :src="require(`../assets/${card.title.icon}-white.svg`)"
        >
        <img
          v-else
          :src="require(`../assets/${card.title.icon}.svg`)"
        >
        {{ card.title.text }}
      </h1>
      <p>{{ card.subtitle }}</p>
      <div :class="checksClass">
        <div
          v-for="(item, cardIndex) in card.infos"
          :key="cardIndex"
        >
          <img
            v-if="card.active"
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
        <span
          v-if="card.price > 0"
          class="not-free"
        >
          R$ {{ card.price }}<span>/month</span>
        </span>
        <span v-else>
          Free Forever
        </span>
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
    card: {
      type: Object,
      default: () => {},
    },
  },
  computed: {
    cardActiveClass() {
      return this.card.active ? 'selected' : '';
    },
    checksClass() {
      return this.card.active ? 'checks-selected' : 'checks';
    },
    chooseButtonClass() {
      return this.card.active ? 'choose-button-active' : 'choose-button';
    },
  },
  methods: {
    clickedCard() {
      this.$emit('cardSelected', this.card.index);
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  max-width: 400px;
  background-color: #ffffff;
  margin: 10px;
  border-radius: 20px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: all 0.8s;
  .info {
    h1 {
      display: flex;
      margin-bottom: 32px;
      img {
        margin-right: 20px;
      }
    }
    p {
      color: #A9A9AA;
      font-size: 22px;
    }

    .checks-selected {
      border-bottom: 1px dashed #ffffff;
      padding: 10px 0px;
    }

    .checks {
      border-bottom: 1px dashed #A9A9AA;
      padding: 10px 0px;
    }

    .checks div, .checks-selected div {
      display: flex;
      justify-content: flex-start;
      align-items: flex-start;
      margin: 24px 0px;
    }

    .checks div span, .checks-selected div span {
      font-size: 18px;
      margin-left: 6px;
    }

    .card-footer {
      display: flex;
      flex-direction: column;
      align-items: center;
      .price {
        width: 100%;
        text-align: left;
        margin-top: 64px;
        margin-bottom: 24px;
        .not-free {
          span {
            font-size: 18px;
            font-weight: 100;
          }
        }
      }

      .choose-button-active, .choose-button {
        width: 100%;
        padding: 20px;
        border-radius: 12px;
        border: none;
        font-size: 22px;
        line-height: 40px;
      }

      .choose-button-active {
        background: #ff1d89;
        box-shadow: 0px 12px 32px rgba(255, 29, 137, 0.5);
        color: #ffffff;
        font-weight: 600;
        cursor: pointer;
      }

      .choose-button {
        background: #FFF5FA;
        color: #ff1d89;
        font-weight: 600;
        cursor: pointer;
      }
    }
  }
}

.card:hover {
  border: 1px solid #0B0641;
}

.selected {
  background-color: #0B0641;
  transform: translateY(-40px);
  color: #ffffff;
  transition: border 0.3s;
}

.selected:hover {
  border: 1px solid #ff1d89;
}
</style>
