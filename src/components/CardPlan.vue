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
  background-color: $white;
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
      color: $gray;
      font-size: 22px;
    }

    .checks-selected {
      border-bottom: 1px dashed $white;
      padding: 10px 0px;
    }

    .checks {
      border-bottom: 1px dashed $gray;
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
        background: $pink;
        box-shadow: 0px 12px 32px $color_box_shadow_button_active;
        color: $white;
        font-weight: 600;
        cursor: pointer;
      }

      .choose-button {
        background: $light;
        color: $pink;
        font-weight: 600;
        cursor: pointer;
      }
    }
  }
}

.card:hover {
  border: 1px solid $background_active;
}

.selected {
  background-color: $background_active;
  transform: translateY(-40px);
  color: $light;
  transition: border 0.3s;
}

.selected:hover {
  border: 1px solid #ff1d89;
}
</style>
