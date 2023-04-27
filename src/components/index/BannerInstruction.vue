<template>
  <section class="banner-instruction" id="banner-instruction">
    <div class="banner-instruction__container container">
      <div class="banner-instruction__content">
        <LogoComponent
          class="banner-instruction__logo"
          :color="'#55B03B'"
        />
        <h3 class="banner-instruction__title title title--bold">
          Скачайте подробную инструкцию по уходу <span class="green">за вашим бассейном</span>
        </h3>
        <p class="banner-instruction__text">Идеальной воды в бассейне можно добиться только при выполнении всех этих
          этапов. Каждый препарат по отдельности не дает исчерпывающего результата</p>
        <div class="banner-instruction__button-group">
          <a href="#" download>
            <button-default
              :text="'Скачать (PDF)'"
              :color="'green'"
            />
          </a>
          <p>Отправляя форму вы соглашаетесь с политикой конфеденциальности и правом на обраотку данных!</p>
        </div>
        <img src="/images/banner/pool.png" alt="">
      </div>
      <div class="banner-instruction__play-video">
        <p>Посмотрите видео о нашем продукте</p>
        <button-play/>
      </div>
    </div>
  </section>
</template>

<script>
import ButtonDefault from '../ui/ButtonDefault.vue'
import LogoComponent from '../ui/LogoComponent.vue'
import ButtonPlay from '../ui/ButtonPlay.vue'

export default {
  components: {
    ButtonDefault,
    LogoComponent,
    ButtonPlay
  }
}
</script>

<style lang="scss" scoped>
.banner-instruction {
  background: url(/src/assets/images/banner/background.jpg);

  &__container {
    position: relative;
    max-width: 450px;
  }

  &__content {
    display: block;
    position: relative;
    padding-bottom: 60px;
    z-index: 1;

    &::before {
      content: '';
      background-color: $baseColor;
      height: 441px;
      width: 100%;
      position: absolute;
      top: -56px;
      left: 50%;
      transform: translateX(-50%);
      z-index: -1;
      border-radius: 50px;
    }

    & img {
      display: none;
    }
  }

  &__logo {
    display: none;
  }

  &__title {
    max-width: 300px;
    margin-left: 16px;
  }

  &__text {
    font-family: 'OpenSansReg';
    color: $secondaryTextColor;
    font-weight: 400;
    font-size: 14px;
    line-height: 26px;
    display: flex;
    align-items: flex-start;
    margin-top: 16px;
    margin-bottom: 24px;
    max-width: 350px;
    padding-left: 16px;

    &::before {
      content: '';
      min-width: 32px;
      height: 1px;
      background-color: $secondaryTextColor;
      margin-top: 12px;
      margin-left: 3px;
      margin-right: 12px;
    }
  }

  &__button-group {
    display: flex;
    flex-direction: column;
    padding: 0 16px;

    & button {
      width: 100%;
    }

    & p {
      font-size: 10px;
      line-height: 15px;
      color: #AEAEAE;
      margin-top: 12px;
      text-align: center;
    }
  }

  &__play-video {
    display: none;
  }

  @media (min-width: $tablet-min) {
    &__container {
      max-width: 1466px;
    }
    &__text {
      font-size: 14px;
      line-height: 26px;
      margin-top: 30px;
      margin-bottom: 32px;
      max-width: 78%;
      padding-left: 93px;

      &::before {
        min-width: 66px;
        margin-right: 22px;
      }
    }
    &__content {
      max-width: 1192px;
      padding-bottom: 114px;

      &::before,
      &::after {
        content: '';
        background-color: $baseColor;
        height: 380px;
        position: absolute;
        top: -56px;
        z-index: -1;
        transform: translateX(0);
      }

      &::before {
        width: 60%;
        border-radius: 50px 0 0 50px;
        left: 0;
      }

      &::after {
        width: 50%;
        transform: skew(-15deg);
        border-radius: 0 50px 50px 0;
        right: 40px;
      }

      & img {
        position: absolute;
        width: 46%;
        bottom: -20%;
        right: -24%;
        transform: translate(-50%, -50%);
      }
    }
    & *[class] {
      z-index: 10;
    }
    &__logo {
      width: 157px;
      height: 92px;
      position: absolute;
      right: 111px;
      top: 7px;
    }
    &__title {
      max-width: 51%;
      padding-left: 93px;
      margin-left: 0;
    }
    &__button-group {
      max-width: 560px;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      padding: 0px 0 0 96px;

      & button {
        min-width: 256px;
        max-width: 256px;
        margin-right: 16px;
      }

      & p {
        text-align: left;
      }
    }
    &__play-video {
      display: flex;
      align-items: center;
      position: absolute;
      right: 12%;
      top: 10px;

      & p {
        font-size: 12px;
        line-height: 16px;
        text-align: right;
        color: #565656;
        max-width: 102px;
        margin-right: 19px;
      }
    }
  }
  @media (min-width: $desktop) {
    padding-top: 84px;
    &__text {
      font-size: 17px;
      margin-bottom: 40px;
      margin-top: 27px;
      padding-left: 95px;
      max-width: 661px;
    }
    &__content {
      padding-bottom: 201px;

      &::before,
      &::after {
        transform: translateX(0);
        height: 441px;

      }

      &::before {
        left: 0;
      }

      &::after {
        right: 100px;
      }

      & img {
        display: flex;
        right: -56.5%;
        width: auto;
      }
    }
    &__title {
      max-width: 815px;
    }
    &__button-group {
      & p {
        margin-top: 4px;
        margin-left: 24px;
      }

      & button {
        height: 70px;
      }
    }
    &__logo {
      display: flex;
    }
    &__play-video {
      flex-direction: column-reverse;
      align-items: flex-end;
      right: 4px;
      top: 12px;

      & p {
        margin-right: 0;
        margin-top: 5px;
      }
    }
  }
  @media (min-width: 1400px) {
    &__play-video {
      flex-direction: row;
      align-items: flex-start;
      top: 27px;

      & p {
        margin-right: 19px;
      }
    }
  }
}
</style>
