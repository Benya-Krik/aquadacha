<template>
  <section class="main" id="main">
    <div class="container main__container">
      <div class="main__background">
        <div class="main__background--wrap"><img src="/images/main/landspace.png" alt=""></div>
        <div class="main__mouse-background">
          <svg width="107" height="32" viewBox="0 0 107 32" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path fill-rule="evenodd" clip-rule="evenodd"
                  d="M106.881 31.3599C72.4177 31.3599 80.734 0 52.5797 0C23.4671 0 35.6164 31.3599 0.0128174 31.3599H106.892H106.881Z"
                  fill="#FBFBFB"/>
            <path fill-rule="evenodd" clip-rule="evenodd"
                  d="M52.9998 12C49.7002 12 47.0005 14.5147 47.0005 17.5882V25.4118C47.0005 28.4853 49.7002 31 52.9998 31C56.2995 31 58.9992 28.4853 58.9992 25.4118V17.5882C58.9992 14.5147 56.2995 12 52.9998 12ZM57.7565 25.4118C57.7565 27.8466 55.6139 29.8424 52.9998 29.8424C50.3858 29.8424 48.2432 27.8466 48.2432 25.4118V17.5882C48.2432 15.1534 50.3858 13.1576 52.9998 13.1576C55.6139 13.1576 57.7565 15.1534 57.7565 17.5882V25.4118Z"
                  fill="#565656"/>
            <path fill-rule="evenodd" clip-rule="evenodd"
                  d="M53 15.792C52.6571 15.792 52.4 16.0315 52.4 16.3508V18.9853C52.4 19.3046 52.6571 19.5441 53 19.5441C53.3428 19.5441 53.5999 19.3046 53.5999 18.9853V16.3508C53.5999 16.0315 53.3428 15.792 53 15.792Z"
                  fill="#565656"/>
          </svg>
        </div>
        <div class="main__content">
          <div class="main__left">
            <button-play/>
            <p>Посмотрите видео о нашем продукте</p>
          </div>
          <div class="main__center">
            <h1 class="main__title title title--bold">Идеальная вода в вашем бассейне - вместе со средствами
              «АкваДача»</h1>
            <p>Подходит для надувных и каркасных бассейнов на даче и в частном доме.</p>
            <div class="main__quiz">
              <button-default
                :color="'green'"
                :text="'Подобрать средство для бассейна'"
                @click="openPopup('quiz')"
              />
              <h3 class="main__button--text title title--medium">Ответьте <span class="green">на 5 вопросов!</span></h3>
              <p class="main__button--description">и получите список средств + советы по уходу за бассейном</p>
            </div>
          </div>
          <div class="main__right">
            <div class="main__contacts">
              <a href="tel:+79020000000"><h2>+7 902 000 00 00</h2></a>
              <a href="mailto:info@aquadacha.ru"><p>info@aquadacha.ru</p></a>
            </div>
            <div class="main__feedback">
              <button-default
                :color="'blue'"
                :text="'Заказать звонок'"
                :svg="'phone'"
                @click="openPopup('request')"
              />
            </div>
          </div>
        </div>
      </div>
      <div class="main__bath"><img src="/images/main/pool.png" alt=""></div>
      <h2 class="main__title--bottom title title--bold">Средства по уходу за водой в бассейне</h2>
    </div>
    <div class="main__benefits">
      <ul class="main__list">
        <li v-for="(benefit, index) in benefits" :key="index">
          <benefit-card
            :title="benefit.title"
            :text="benefit.text"
          />
        </li>
      </ul>
    </div>
    <popup-component
      :isOpened="isOpened"
      :dataPopup="dataPopup"
      :isQuizPopup="isQuizPopup"
      @open-popup="openPopup"
      @close-popup="closePopup"
      @nextStep="nextStep(false)"
    />
    <request-popup
      :isRequestPopup="isRequestPopup"
      @open-popup="openPopup"
      @close-popup="closePopup"
    />
    <success-popup
      :isSuccessPopup="isSuccessPopup"
      @open-popup="openPopup"
      @close-popup="closePopup"
    />
  </section>
</template>

<script>
import PopupComponent from '../blocks/PopupComponent.vue'
import ButtonDefault from '../ui/ButtonDefault.vue'
import ButtonPlay from '../ui/ButtonPlay.vue'
import BenefitCard from '../blocks/BenefitCard.vue'
import RequestPopup from '@/components/blocks/RequestPopup'
import SuccessPopup from '@/components/blocks/SuccessPopup'

export default {
  components: {
    SuccessPopup,
    RequestPopup,
    PopupComponent,
    ButtonDefault,
    ButtonPlay,
    BenefitCard
  },
  data () {
    return {
      isOpened: false,
      dataPopup: {},
      isQuizPopup: true,
      isRequestPopup: false,
      isSuccessPopup: false,
      benefits: [
        {
          title: 'Удобный формат',
          text: 'средства - хватит на весь сезон'
        },
        {
          title: 'Адаптировано',
          text: 'к воде бассейнов РФ'
        },
        {
          title: 'Изготовлено',
          text: 'в соответствии ГОСТам и СанПиН'
        },
        {
          title: 'Вся продукция',
          text: 'прошла гос. сертификацию'
        }
      ],
      scrollWidth: 0
    }
  },
  created () {
    this.widthScrollBar()
  },
  methods: {
    widthScrollBar () {
      const div = document.createElement('div')
      div.style.overflowY = 'scroll'
      div.style.width = '50px'
      div.style.height = '50px'
      document.body.append(div)
      const scrollWidth = div.offsetWidth - div.clientWidth
      div.remove()
      this.scrollWidth = `${scrollWidth}px`
    },
    scrollBarVisibility () {
      if (this.isProductPopup || this.isRequestPopup || this.isSuccessPopup) {
        document.querySelector('html').classList.add('opened')
        document.querySelector('html').style.marginRight = this.scrollWidth
        document.querySelector('header').style.marginRight = this.scrollWidth
      } else {
        document.querySelector('html').classList.remove('opened')
        document.querySelector('html').style.marginRight = '0px'
        document.querySelector('header').style.marginRight = '0px'
      }
    },
    closePopup (popup, data) {
      this.isOpened = false
      this.isQuizPopup = false
      this.isRequestPopup = false
      this.isSuccessPopup = false
      this.scrollBarVisibility()
      this.nextStep()
      if (popup === 'success') {
        this.isSuccessPopup = true
      }
    },
    openPopup (popup) {
      console.log(popup)
      switch (popup) {
        case 'quiz':
          this.isOpened = true
          this.isQuizPopup = true
          break
        case 'request':
          this.isRequestPopup = true
          break
      }
      this.scrollBarVisibility()
    },
    nextStep (value) {
      this.isQuizStart = value
    }
  }
}
</script>

<style lang="scss" scoped>
.main {
  background-image: url(/src/assets/images/main/background.png);
  background-size: cover;
  background-repeat: no-repeat;
  padding-top: 48px;

  &__background {
    &--wrap {
      display: none;
    }
  }

  &__mouse-background,
  &__bath,
  &__left {
    display: none;
  }

  &__content {
    margin-top: 40px;
  }

  &__title {
    margin-bottom: 16px;

    &--bottom {
      margin-top: 12px;
    }
  }

  &__quiz {
    margin-top: 28px;
    background-color: $baseColor;
    border-radius: 50px;
    padding: 24px 16px;
    display: flex;
    flex-direction: column;
    align-items: center;

    & h3 {
      margin-top: 16px;
    }

    p {
      display: block;
      margin-top: 8px;
      font-size: 14px;
      text-align: center;
    }
  }

  &__contacts {
    display: none;
  }

  &__feedback {
    margin-top: 16px;
  }

  &__benefits {
    margin: 16px 16px 0;
  }

  &__list {
    display: grid;
    grid-template-columns: 200px 200px 200px 200px;
    grid-column-gap: 16px;
    overflow-x: scroll;
  }

  @media (min-width: $mobile-max) {
    &__feedback {
      max-width: 344px;
      margin: 16px auto 0;
    }
  }
  @media (min-width: $tablet-min) {
    &__mouse-background,
    &__bath,
    &__left {
      display: block;
    }
    &__container {
      position: relative;
      height: 100%;
      display: flex;
      flex-direction: column;
      align-items: flex-end;
    }
    &__background {
      position: relative;
      display: block;
      width: 100%;
      height: 100%;
      max-height: 800px;
      border-radius: 0 0 60px 60px;
      overflow: hidden;
      z-index: 0;

      &--wrap {
        display: block;
      }
    }
    &__bath {
      display: block;
      position: absolute;
      width: 50%;
      top: 73%;
      left: 107px;
      & img {
        width: 100%;
      }
    }
    &__mouse {
      position: absolute;
      top: 8px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      justify-content: center;

      & img {
        width: 11px;
      }
    }
    &__mouse-background {
      position: absolute;
      bottom: -1px;
      left: 65%;
      display: flex;
      justify-content: center;
    }
    &__content {
      position: absolute;
      top: 0;
      width: 100%;
      height: 100%;
      z-index: 100;
      grid-gap: 0;
      display: grid;
      grid-template-columns: 1fr 4fr 2fr;
      align-items: baseline;
      margin-top: 0;
      padding: 30px 12px 18px 12px;
    }
    &__title {
      font-weight: 700;
      color: #1b1b1b;
      letter-spacing: 0.41px;
      max-width: 550px;
      font-size: 24px;
      line-height: 30px;

      &--bottom {
        width: 100%;
        color: #010101;
        opacity: 0.9;
        max-width: 300px;
        text-align: right;
      }
    }
    &__quiz {
      max-width: 84%;
      padding: 16px 20px;
      border-radius: 58px;
      margin-top: 0;
      overflow: hidden;

      & button {
        font-size: 15px;
        font-family: 'OpenSansBold';
      }

      &--text {
        font-size: 17px;
        font-weight: 700;
        color: #2e2e2e;
        margin-top: 12px;
        letter-spacing: 0.56px;

        & span {
          color: #54af3a;
        }
      }

      &--description {
        text-align: center;
        font-size: 13px;
        font-weight: 400;
      }

      & h3 {
        margin-bottom: 0px;
        margin-top: 8px;

      }

      & p {
        line-height: 18px;
        margin-top: 0;
      }
    }
    &__right {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-self: end;
      height: 100%;
      justify-content: space-between;
      align-items: flex-end;
    }
    &__contacts {
      display: flex;
      flex-direction: column;
      align-items: flex-end;

      & a {
        transition: all .5s ease;
        &:hover {
          opacity: .7;
        }
      }

      & h2 {
        color: #000000;
        font-size: 24px;
        font-weight: 700;
        letter-spacing: 0.2px;
      }

      & p {
        font-size: 15px;
        font-weight: 400;
        color: #000000;
        opacity: 0.6;
      }
    }
    &__feedback {
      position: absolute;
      bottom: 55px;

      & button {
        display: flex;
        justify-content: center;
        align-items: center;
        grid-gap: 8px;
        padding: 12px 24px;

        & p {
          color: #ffffff;
          font-size: 15px;
          font-weight: 400;
        }
      }
    }
    &__left {
      max-width: 115px;
      align-self: flex-end;
      display: flex;
      flex-direction: column;
      align-items: flex-start;

      & p {
        font-size: 12px;
        font-weight: 400;
        opacity: 0.9;
        color: #353535;
        max-width: 98px;
      }
    }
    &__center {
      display: flex;
      flex-direction: column;

      & > p {
        font-size: 17px;
        font-weight: 400;
        letter-spacing: 0.2px;
        color: #0f0f0f;
        max-width: 370px;
        margin-bottom: 16px;
        position: relative;
        display: flex;
        align-items: flex-start;
        justify-content: flex-end;

        &::before {
          content: '';
          width: 20%;
          height: 1px;
          background-color: #1e1e1e;
          top: 12px;
          margin-right: 20px;
          margin-top: 10px;
        }
      }
    }
    &__benefits {
      margin-top: 84px;
      width: 100%;
      margin-bottom: 64px;
    }
    &__list {
      grid-template-columns: 1fr 1fr 1fr 1fr;
      grid-column-gap: 8px;
      overflow: visible;
    }
  }
  @media (min-width: $tablet-max) {
  }
  @media (min-width: $desktop) {
    &__background {
      max-height: 817px;

      &--wrap {
        height: 100%;

        & img {
          height: 100%;
        }
      }
    }
    &__content {
      padding: 0;
      align-items: flex-start;
    }
    &__container {
      padding-right: 0;
    }
    &__mouse-background {
      left: 68%;
    }
    &__bath {
      width: 49%;
      top: 68.5%;
      left: 129px;
    }
    &__title {
      font-size: 40px;
      line-height: 54px;
      letter-spacing: 0;
      margin-bottom: 24px;

      &--bottom {
        max-width: 450px;
        margin-top: 24px;
        font-size: 36px;
        line-height: 46px;
      }
    }
    &__quiz {
      margin-left: 2px;
      max-width: 60%;
      padding-bottom: 18px;

      & button {
        height: 72px;
        padding-bottom: 4px;
        font-size: 16px;
      }

      & h3 {
        margin-bottom: 0;
        margin-top: 14px;
      }

      & p {
        margin-top: 5px;
        letter-spacing: -.4px;
        font-size: 13px;
        max-width: 90%;
      }
    }
    &__feedback {
      bottom: 36px;
      right: 55px;

      & button {
        height: 58px;
        padding: 12px 37px 12px 40px;
        font-size: 14px;
        letter-spacing: .5px;

        &::before {
          font-size: 11px;
          margin-right: 0;
        }
      }

    }
    &__left {
      display: block;
      margin-left: 57px;
      padding-bottom: 80px;
      grid-gap: 16px;

      & svg {
        width: 60px;
        height: 60px;
      }

      & p {
        font-size: 12px;
        max-width: 89px;
        letter-spacing: .2px;
        line-height: 16px;
      }
    }
    &__center {
      margin-top: 75px;
      padding-left: 32px;

      & > p {
        margin-left: 3px;
        max-width: 486px;
        margin-bottom: 22px;

        &::before {
          width: 21%;
          margin-right: 21px;
        }
      }
    }
    &__list {
      grid-column-gap: 54px;
    }
    &__contacts {
      margin-right: 68px;
      margin-top: 80px;

      & h2 {
        font-size: 27px;
        letter-spacing: -.4px;
        line-height: 39px;
      }

      & p {
        letter-spacing: .4px;
      }
    }
    &__benefits {
      grid-column-gap: 28px;
      margin: 133px auto 87px;
      padding: 0 20px;
      width: 100%;
      max-width: 1466px;
    }
  }
  @media (min-width: 1400px) {
    &__quiz {
      & button {
        font-size: 18px;
      }
    }
    &__title {
      &--bottom {
        font-size: 40px;
        line-height: 54px;
        margin-top: 40px;
      }
    }
    &__bath {
      width: 53%;
      top: 68.5%;
      left: 129px;
    }
    &__benefits {
      grid-column-gap: 54px;
    }
  }
}

/* @media screen and (max-width: 1500px) {
    .main {
        &__content {
            padding: 64px 59px 48px 80px;
        }

        &__background {
            &--wrap {
                padding: 0 48px;
                top: 0;
            }
        }
    }
}

@media screen and (max-width: 980px) {
    .main {
        &__content {
            padding: 64px 20px 48px 80px;
            grid-template-columns: 1fr 4fr 3fr;
        }
        &__bath {
            display: none;
        }
    }
} */

/* @media screen and (max-width: 880px) {
    .main {
        &__quiz {
            display: flex;
            flex-direction: column;
            max-width: 478px;
            background-color: #FFFFFF;
            padding: 14px 8px 18px 8px;
            border-radius: 58px;
            display: flex;
            flex-direction: column;
            align-items: center;
            &--text {
                font-size: 14px;
                font-weight: 700;
                color: #2e2e2e;
                margin-top: 12px;
                letter-spacing: 0.56px;
                & span {
                    color: #54af3a;
                }
            }
            &--description {
                text-align: center;
                font-size: 13px;
                font-weight: 400;
            }
            & button {
                padding: 12px 20px;
                font-size: 14px;
            }
        }
    }
}

@media screen and (max-width: 880px) {
    .main {
        &__quiz {
            display: flex;
            flex-direction: column;
            max-width: 478px;
            background-color: #FFFFFF;
            padding: 14px 8px 18px 8px;
            border-radius: 58px;
            display: flex;
            flex-direction: column;
            align-items: center;
            &--text {
                font-size: 14px;
                font-weight: 700;
                color: #2e2e2e;
                margin-top: 12px;
                letter-spacing: 0.56px;
                & span {
                    color: #54af3a;
                }
            }
            &--description {
                text-align: center;
                font-size: 13px;
                font-weight: 400;
            }
            & button {
                padding: 12px 20px;
                font-size: 14px;
            }
        }
    }
}

@media screen and (max-width: 800px) {
    .main {
        &__mouse {
            display: none;
            &--background {
                display: none;
            }
        }
    }
}

@media screen and (max-width: 1024px) {
    .main {
        &__title {
            font-size: 24px;
            line-height: 26px;
            &--bottom {
                font-size: 24px;
                line-height: 26px;
                max-width: 400px;
                padding-top: 40px;
            }
        }
        &__right {
            &--contacts {
                & h2 {
                    font-size: 24px;
                    line-height: 26px;
                }
            }
        }
    }
}

@media screen and (max-width: 700px) {
    .main {
        &__container {
            align-items: center;
        }
        &__left {
            background-color: #FFFFFF;
            padding: 20px;
            align-self: center;
            max-width: 100%;
            order: 3;
            align-items: center;
            flex-direction: row;
            border-radius: 58px;
            & p {
                text-align: center;
            }
        }

        &__title {
            font-size: 20px;
            font-weight: 900;
            letter-spacing: normal;
            text-align: center;
            &--bottom {
                font-size: 20px;
                letter-spacing: 0;
                font-weight: 900;
                text-align: center;
                padding: 16px 0px 40px 0;
            }
        }

        &__background {
            &--wrap {
                // display: none;
                position: absolute;
                left: -300px;
                z-index: -1;
            }
        }

        &__content {
            display: flex;
            position: static;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 40px 0;
            grid-gap: 20px;
        }

        &__center {
            align-items: center;
        }

        &__right {
            justify-content: center;
            height: auto;
            grid-gap: 20px;
            &--contacts {
                align-items: center;
            }
        }

        &__description {
            display: flex;
            text-align: center;
            margin: 12px 0 12px 32px;
            font-size: 16px;
            &::before {
                content: '';
                position: absolute;
                width: 20px;
                height: 2px;
                background-color: #1e1e1e;
                top: 12px;
                left: -18px;
            }
        }
        &__quiz {
            &--description {
                max-width: 340px;
            }
        }
    }
} */
</style>
