<template>
    <section class="popup" v-if="isOpened">
      <div class="popup__area" @click="closePopup"></div>
      <transition name="fade" mode="out-in" appear>
        <div class="popup__container container">
          <button class="popup__button button button--close" @click="closePopup"></button>
          <LogoComponent class="popup__logo" :color="'#55B03B'"/>
          <template>
            <product-popup
              v-if="isProductPopup"
              :dataPopup="dataPopup"
              @close-popup="$emit('closePopup', 'request')"
            />
            <quiz-start
              v-if="isQuizPopup && isQuizStart"
              @to-next-step="toNextStep('isQuizStep1')"
            />
            <quiz-step-1
              v-if="isQuizStep1"
              @to-next-step="toNextStep('isQuizStep2')"
              @back="toNextStep('isQuizStart')"
            />
            <quiz-step-2
              v-if="isQuizStep2"
              @to-next-step="toNextStep('isQuizStep3')"
              @back="toNextStep('isQuizStep1')"
            />
            <quiz-step-3
              v-if="isQuizStep3"
              @to-next-step="toNextStep('isQuizFinish')"
              @back="toNextStep('isQuizStep2')"
            />
            <quiz-finish
              v-if="isQuizFinish"
              @closePopup="closePopup"
              @back="toNextStep('isQuizStep3')"
            />
          </template>
        </div>
      </transition>
    </section>
</template>

<script>
import LogoComponent from '../ui/LogoComponent.vue'
import ProductPopup from '../blocks/ProductPopup.vue'
import QuizStart from '../blocks/quiz/QuizStart.vue'
import QuizStep1 from '../blocks/quiz/QuizStep1.vue'
import QuizStep2 from '../blocks/quiz/QuizStep2.vue'
import QuizStep3 from '../blocks/quiz/QuizStep3.vue'
import QuizFinish from '../blocks/quiz/QuizFinish.vue'

export default {
  props: ['isOpened', 'dataPopup', 'isProductPopup', 'isQuizPopup'],
  components: {
    LogoComponent,
    ProductPopup,
    QuizStart,
    QuizStep1,
    QuizStep2,
    QuizStep3,
    QuizFinish
  },
  data () {
    return {
      isQuizStart: true,
      isQuizStep1: false,
      isQuizStep2: false,
      isQuizStep3: false,
      isQuizFinish: false
    }
  },
  methods: {
    resetSteps () {
      this.isQuizStart = false
      this.isQuizStep1 = false
      this.isQuizStep2 = false
      this.isQuizStep3 = false
      this.isQuizFinish = false
    },
    closePopup () {
      this.resetSteps()
      this.$emit('closePopup')
      this.isQuizStart = true
    },
    toNextStep (activeStep) {
      this.resetSteps()
      switch (activeStep) {
        case 'isQuizStart':
          this.isQuizStart = true
          break
        case 'isQuizStep1':
          this.isQuizStep1 = true
          break
        case 'isQuizStep2':
          this.isQuizStep2 = true
          break
        case 'isQuizStep3':
          this.isQuizStep3 = true
          break
        case 'isQuizFinish':
          this.isQuizFinish = true
          break
      }
    }
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

.popup {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 102;
  background-color: rgba(180, 180, 180, .4);
  transition: all .5s ease;
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
  }

  &__logo {
    display: none;
  }

  @media (min-width: $tablet-min) {
    &__container {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background-color: $baseColor;
      border-radius: 84px;
      overflow-y: visible;
      max-width: 1197px;
      height: 624px;
      padding: 58px 72px 50px;
    }
    &__logo {
      position: absolute;
      display: block;
      max-width: 112px;
      right: 72px;
      z-index: 10;
      top: 48px;
    }
  }
  @media (min-width: $desktop) {
    &__container {
      //position: absolute;
      //top: 50%;
      //left: 50%;
      //transform: translate(-50%, -50%);
      //background-color: $baseColor;
      //max-width: 1200px;
      //height: 570px;
      //padding: 50px;
    }
    &__logo {
      //position: absolute;
      //right: 50px;
      //z-index: 10;
    }
  }
}

template {
  display: block;
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
      top: -2px;
      border: 2px solid $baseColor;
      &::before,
      &::after {
        background-color: $baseColor;
      }
    }
    @media (min-width: $desktop) {
      right: -7px;
      top: -2px;
    }
  }
}
</style>
