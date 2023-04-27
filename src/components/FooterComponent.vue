<template>
  <footer class="footer">
    <div class="footer__top">
      <div class="footer__container container">
        <a class="footer__logo" href="#main">
          <logo-component
            :color="'#ffffff'"
          />
        </a>
        <ul class="footer__menu menu">
          <li><a href="#benefits">Преимущества</a></li>
          <li><a href="#products">Продукция</a></li>
          <li><a href="#banner-form">Приобрести</a></li>
          <li><a href="#problems">Частые проблемы</a></li>
          <li><a href="#banner-instruction">Подобрать средство</a></li>
        </ul>
        <div class="footer__contacts">
          <a href="tel:+79020000000">
            +7 902 000 00 00
          </a>
          <a href="mailto:info@aquadacha.ru">
            info@aquadacha.ru
          </a>
        </div>
      </div>
    </div>
    <div class="footer__bottom">
      <div class="footer__container container">
        <p class="footer__company">©2022 ООО «АКВАДАЧА»</p>
        <h3 class="footer__title title title--medium">Средства по уходу за водой в бассейне</h3>
        <div class="footer__social">
          <a class="vk" href="#">
          </a>
          <a class="youtube" href="#">
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import LogoComponent from './ui/LogoComponent.vue'

export default {
  components: {
    LogoComponent
  }
}
</script>

<style lang="scss" scoped>
.footer {
  background-color: $mainColor;
  color: $baseColor;

  &__logo {
    & > svg {
      max-width: 109px;
      display: block;
    }
  }

  &__menu {
    display: none;
  }

  &__contacts {
    text-align: right;
    display: flex;
    flex-direction: column;
  }

  &__top {
    border-bottom: 1px solid $baseColor;

    & .footer__container {
      padding-top: 32px;
      padding-bottom: 32px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
  }

  &__bottom {
    padding-top: 22px;
    padding-bottom: 23px;

    & .footer__container {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-direction: column;
    }
  }

  &__company {
    font-size: 12px;
    line-height: 18px;
    text-align: right;
  }

  &__title {
    color: $baseColor;
    text-transform: uppercase;
    margin: 12px 0;
  }

  &__social {
    & a + a {
      margin-left: 15px;
    }
  }

  @media (min-width: $tablet-min) {
    &__logo {
      & > svg {
        margin-right: 76px;
      }
    }
    &__contacts {
      margin-left: 90px;
    }
    &__bottom {
      & .footer__container {
        flex-direction: row;
      }
    }
    &__title {
      margin: 0;
    }
  }
  @media (min-width: $desktop) {
    &__logo {
      & > svg {
        margin-right: 76px;
      }
    }
    &__menu {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    &__top {
      & .footer__container {
        padding-top: 57px;
        padding-bottom: 64px;
      }
    }
  }
}
</style>
