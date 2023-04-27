<template>
  <div class="product-popup">
    <h3 class="product-popup__title title title--bold">{{ dataPopup.title }}</h3>
    <p class="product-popup__benefit">{{ dataPopup.benefit }}</p>
    <div class="product-popup__content">
      <div class="product-popup__left">
        <div class="product-popup__image">
          <img :src="dataPopup.image" alt="">
        </div>
      </div>
      <div class="product-popup__right">
        <ul class="product-popup__list">
          <li v-for="(item, index) in dataPopup.specification" :key="index">
            <h4 class="product-popup__title title title--small">{{ item.title }}</h4>
            <p>{{ item.text }}</p>
          </li>
        </ul>
      </div>
    </div>
    <div class="product-popup__buy">
      <p class="product-popup__price">
        Цена: <span class="green"> {{ dataPopup.price }} руб</span>
      </p>
      <button-default
        class="product-popup__button"
        :color="'green'"
        :text="'Купить'"
        @click="$emit('closePopup', 'request')"
      />
    </div>
  </div>
</template>

<script>
import ButtonDefault from '../ui/ButtonDefault.vue'

export default {
  props: ['dataPopup'],
  components: {
    ButtonDefault
  }
}
</script>

<style lang="scss" scoped>
.product-popup {
  h3 {
    margin-bottom: 8px;
    text-align: center;
  }

  &__content {
    margin-top: 48px;
  }

  &__right {
    margin-top: 16px;
    margin-bottom: 16px;
    & li {
      font-size: 14px;
    }
    & h4 {
      text-align: left;
      font-size: 17px;
      margin-bottom: 6px;
    }

    & li + li {
      margin-top: 23px;
    }
  }

  &__button {
    width: 100%;
  }

  &__price {
    margin-bottom: 12px;
    & span.green {
      font-family: 'OpenSansBold';
      color: $mainColor;
      font-size: 31px;
      margin-left: 8px;
    }
  }

  &__buy {
    display: flex;
    flex-direction: column;
    margin-top: 24px;
  }

  &__image {
    width: 100%;
    margin-top: 16px;
    & img {
      width: 100%;
    }
  }

  &__benefit {
    letter-spacing: 1.6px;
    text-align: center;
  }

  @media (min-width: $tablet-min) {
    h3 {
      margin-left: 24px;
      max-width: 70%;
      margin-bottom: 8px;
      text-align: left;
    }
    &__benefit {
      margin-left: 24px;
      text-align: left;
      font-size: 22px;
      margin-top: 10px;
    }
    &__content {
      display: flex;
      align-items: flex-end;
      margin-top: 34px;
    }
    &__left {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      margin-right: 62px;
    }
    &__right {
      & li + li {
        margin-top: 22px;
      }
    }
    &__button {
      max-width: 207px;
      font-size: 19px;
      letter-spacing: 0.6px;
    }
    &__price {
      margin-left: 37px;
      width: 270px;
      margin-right: 20px;
      margin-bottom: 0;
    }
    &__buy {
      flex-direction: row;
      align-items: center;
    }
    &__image {
      width: 270px;
    }
  }
  @media (min-width: $desktop) {
    & h3 {
      max-width: 70%;
      margin-bottom: 8px;
    }
    &__content {
      display: flex;
    }
    &__left {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
    &__price {
      width: 270px;
    }
    &__buy {
      display: flex;
    }
    &__image {
      width: 270px;
    }
  }
}
</style>
