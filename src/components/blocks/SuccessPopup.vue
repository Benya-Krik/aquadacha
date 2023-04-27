<template>
    <section class="popup-request" v-if="isSuccessPopup">
      <div class="popup-request__area" @click="$emit('closePopup')"></div>
      <transition name="fade" mode="out-in" appear>

      <div class="popup-request__container container">
        <button class="popup-request__button button button--close" @click="$emit('closePopup')"></button>
        <LogoComponent class="popup-request__logo" :color="'#55B03B'"/>
        <h2 class="popup-request__title title title--bold">Спасибо! Ваша заявка принята!</h2>
        <p class="popup-request__description">Мы свяжемся с вами в течение 15 минут и сообщим стоимость. Пока можете почитать методы по уходу за бассейном</p>
        <div class="popup-request__button-group">
          <button-default
            :color="'green'"
            :text="'Посмотреть каталог'"
            @click="$emit('closePopup')"
          />
        </div>
      </div>
      </transition>

    </section>
</template>

<script>
import LogoComponent from '../ui/LogoComponent.vue'
import ButtonDefault from '@/components/ui/ButtonDefault'

export default {
  props: ['isSuccessPopup'],
  components: {
    ButtonDefault,
    LogoComponent
  }
}
</script>

<style lang="scss" scoped>

.fade-enter-active {
  animation: opened .5s;
}

.fade-leave-active {
  animation: closed .5s;
}

@keyframes opened {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes closed {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

.popup-request {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 102;
  background-color: rgba(180, 180, 180, .4);

  &__area {
    position: absolute;
    width: 100vw;
    height: 100vh;
    backdrop-filter: blur(5px);
    z-index: 0;
    cursor: pointer;
  }

  &__container {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    padding: 32px 20px;
    overflow-y: scroll;
    max-width: none;
    background-color: $baseColor;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  &__logo {
    width: 150px;
    height: 79px;
    margin-top: 16px;
  }

  &__title {
    margin-top: 45px;
    letter-spacing: 0.6px;
    margin-left: 11px;
    max-width: 80%;
    font-size: 37px;
    line-height: 46px;
    margin-bottom: 39px;
    text-align: center;
  }

  &__description {
    font-size: 19px;
    max-width: 93%;
    text-align: center;
    line-height: 31px;
  }

  &__form {
    margin-top: 65px;
    max-width: 551px;
  }
  &__button-group {
    width: 366px;
    position: absolute;
    bottom: 59px;
    & button {
      font-size: 21px;
      letter-spacing: 0.2px;
    }
  }
  @media (min-width: $tablet-min) {
    &__container {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background-color: $baseColor;
      max-width: 512px;
      height: 631px;
      border-radius: 87px;
      padding: 50px;
      overflow-y: visible;
    }
    &__logo {
    }
  }
  @media (min-width: $desktop) {
    &__container {
    }
    &__logo {
    }
  }
}

.form {
  display: flex;
  flex-direction: column;
  align-items: center;
  &__top {
    display: flex;
    justify-content: space-between;
    margin-bottom: 18px;
    & div.input {
      max-width: 96%;
      &:first-child {
        margin-right: 16px;
      }
    }
  }
  & .input {
    height: 70px;
    max-height: none;
    position: relative;
  }
  &__agree {
    text-align: center;
    margin-top: 36px;
    font-size: 11px;
    max-width: 307px;
  }
  &__button-group {
    margin-top: 38px;
    width: 366px;
  }
  & button {
    height: 84px;
    font-size: 20px;
  }
}

template {
  display: block;
}

.radio {
  position: absolute;
  top: 37%;
  left: 38px;
  transform: translateX(-50%);
}

.button {
  &--close {
    position: absolute;
    right: 12px;
    top: 12px;
    width: 26px;
    height: 26px;
    border: 2px solid $mainColor;
    border-radius: 50%;
    z-index: 100;
    transition: all .5s ease;
    &::before,
    &::after {
      content: "";
      position: absolute;
      top: 5px;
      right: 10px;
      height: 12px;
      width: 2px;
      background-color: $mainColor;
      border-radius: 5px;
      transition: all .5s ease;
      &:hover {
        opacity: .7;
        transition: all .5s ease;
      }
    }

    &::before {
      transform: rotate(45deg);
    }

    &::after {
      transform: rotate(-45deg);
    }
    &:hover {
      opacity: .7;
      transition: all .5s ease;
    }
    @media (min-width: $tablet-min) {
      right: 0;
      top: 0;
      border: 2px solid $baseColor;
      &::before,
      &::after {
        background-color: $baseColor;
      }
    }
  }
}
</style>
