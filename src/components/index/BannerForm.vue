<template>
  <section class="banner-form" id="banner-form">
    <div class="banner-form__container container">
      <div class="banner-form__content">
        <h2 class="banner-form__title title title--bold">Подберем средство для вашего бассейна</h2>
        <p>Оставьте заявку, мы свяжемся с Вами, уточним все пожелания и направим варианты стоимости</p>
      </div>
      <form action="" class="banner-form__form form">
        <input-component
          class="form__input"
          :placeholder="'Как вас зовут?'"
        />
        <input-component
          :placeholder="'Ваш номер телефона'"
        />
        <div class="banner-form__bottom">
          <button-default
            :text="'Отправьте заявку'"
            :color="'blue'"
          />
          <p>Отправляя форму вы соглашаетесь с политикой конфеденциальности и правом на обраотку данных!</p>
        </div>
      </form>
    </div>
  </section>
</template>

<script>
import ButtonDefault from '../ui/ButtonDefault.vue'
import InputComponent from '../ui/InputComponent.vue'

export default {
  components: {
    InputComponent,
    ButtonDefault
  }
}
</script>

<style lang="scss" scoped>
.banner-form {
  background: url(/src/assets/images/banner-form/background.png);
  width: 100%;
  height: 425px;
  position: relative;

  &__container {
    position: relative;

    &::before {
      content: '';
      background-color: $baseColor;
      height: 460px;
      position: absolute;
      top: 48px;
      left: 50%;
      transform: translateX(-50%);
      width: calc(100% - 40px);
      z-index: 1;
      border-radius: 50px;
      box-shadow: 0px 70px 28px rgba(0, 0, 0, 0.01), 0px 40px 24px rgba(0, 0, 0, 0.02), 0px 18px 18px rgba(0, 0, 0, 0.03), 0px 4px 10px rgba(0, 0, 0, 0.04), 0px 0px 0px rgba(0, 0, 0, 0.04);
    }
  }

  &__content {
    text-align: center;
    position: relative;
    z-index: 2;
    padding: 80px 20px 0;

    & p {
      font-weight: 400;
      font-size: 14px;
      line-height: 20px;
      color: #565656;
      max-width: 352px;
    }
  }

  &__title {
    max-width: 457px;
    margin-bottom: 20px;
    text-align: center;
  }

  &__form {
    position: relative;
    z-index: 2;
    max-width: 453px;
    padding: 24px 20px;

    & input {
      height: 64px;
    }

    & input + input {
      margin-top: 15px;
    }

    &::before {
      content: '';
      background-color: $baseColor;
    }
  }

  &__bottom {
    margin-top: 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    & p {
      max-width: 120px;
      font-weight: 400;
      font-size: 9px;
      line-height: 11px;
      color: #AEAEAE;
      margin-left: 8px;
    }
  }

  @media (min-width: $tablet-min) {
    height: 330px;
    &__container {
      display: block;
      height: 330px;
      display: grid;
      grid-template-columns: 1fr 1fr;

      &::before,
      &::after {
        content: '';
        background-color: $baseColor;
        height: 330px;
        position: absolute;
        top: 57px;
        box-shadow: none;
      }

      &::before {
        width: 60%;
        border-radius: 50px 0 0 50px;
        transform: translateX(0);
        z-index: 1;
        left: 20px;
      }

      &::after {
        width: 50%;
        transform: skew(-15deg);
        border-radius: 0 82px 82px 0;
        right: 40px;
      }
    }
    &__content {
      padding-top: 124px;
      padding-left: 48px;
      text-align: left;
    }
    &__title {
      margin-bottom: 42px;
      text-align: left;
    }
    &__form {
      margin-left: 0;
      max-width: 400px;
      padding: 124px 35px 20px 0;
      & input {
        height: 70px;
      }
    }
    &__bottom {
      padding-right: 15px;

      & p {
        max-width: 116px;
        line-height: 11px;
        margin-left: 19px;
      }
    }
  }
  @media (min-width: $desktop) {
    height: 425px;
    &__container {
      display: block;
      height: 441px;
      display: grid;
      grid-template-columns: 1fr 1fr;
      position: relative;

      &::before,
      &::after {
        content: '';
        background-color: $baseColor;
        height: 441px;
        position: absolute;
        top: 87px;
      }

      &::before {
        width: 60%;
        border-radius: 50px 0 0 50px;
        z-index: 1;
      }

      &::after {
        right: 76px;
      }
    }
    &__content {
      z-index: 2;
      padding-top: 174px;
      padding-left: 95px;

      & p {
        max-width: 360px;
        font-size: 19px;
        line-height: 31px;
        letter-spacing: -.3px;
      }
    }
    &__title {
      max-width: 457px;
      margin-bottom: 38px;
    }
    &__form {
      z-index: 2;
      margin-left: 14px;
      max-width: 472px;
      padding-top: 187px;

      & button {
        height: 70px;
        letter-spacing: 0.3px;
        text-align: left;
        padding-left: 48px;
      }

      & input + input {
        margin-top: 15px;
      }

      &::before {
        content: '';
        background-color: $baseColor;
      }
    }
    &__bottom {
      margin-top: 15px;
      display: flex;
      justify-content: space-between;
      align-items: center;

      & p {
        max-width: 165px;
        font-weight: 400;
        font-size: 9px;
        line-height: 13px;
        color: #AEAEAE;
        margin-left: 19px;
      }
    }
  }
}

.form {
  @media (min-width: 760px) {
    &__input {
      margin-bottom: 15px;
    }
  }
}
</style>
