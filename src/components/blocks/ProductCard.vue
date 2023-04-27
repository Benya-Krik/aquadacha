<template>
  <article class="product">
    <div class="product__image">
      <p>{{ weight }} кг</p>
      <img :src="image" alt="">
    </div>
    <h3 class="product__title title title--medium">{{ title }}</h3>
    <p class="product__description">{{ description }}</p>
    <p class="product__price">Цена:
      <span>{{ price }} руб</span>
    </p>
    <button-default
      class="product__button"
      :text="'Подробнее'"
      :svg="'arrow'"
      :color="'green'"
      @click="$emit('openPopup')"
    />
  </article>
</template>

<script>
import ButtonDefault from '../ui/ButtonDefault.vue'

export default {
  props: ['image', 'title', 'description', 'price', 'weight'],
  components: {
    ButtonDefault
  }
}
</script>

<style lang="scss" scoped>
.product {
  background-color: $baseColor;
  border: 1px solid #d9d9d9;
  border-radius: 10px;
  padding: 21px 31px 28px;
  transition: all .5s ease;
  cursor: pointer;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;

  &:hover {
    box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.25);
  }

  &__image {
    position: relative;
    width: 100%;
    min-height: 267px;

    & p {
      position: absolute;
      z-index: 1;
      right: -7px;
      top: -7px;
      color: #bbbbbb;
      font-size: 15px;
      line-height: 24px;
    }

    & img {
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
    }
  }

  &__title {
    text-align: center;
    max-width: 285px;
    margin-top: 17px;
    font-size: 24px;
    line-height: 29px;
    text-align: center;
    letter-spacing: 0.03em;
  }

  &__description {
    text-align: center;
    max-width: 280px;
    margin-top: 20px;
  }

  &__price {
    margin-top: 18px;
    font-weight: 400;
    font-size: 16px;
    line-height: 26px;
    text-align: center;

    & span {
      font-family: 'OpenSansBold';
      font-weight: 700;
      font-size: 24px;
      line-height: 38px;
      color: $mainColor;
      margin-left: 6px;
    }
  }

  &__button {
    margin-top: 15px;
    font-size: 17px;
    max-width: 240px;
  }

  @media (min-width: $desktop) {
    &__price {
      margin-top: 52px;
    }
  }
}
</style>
