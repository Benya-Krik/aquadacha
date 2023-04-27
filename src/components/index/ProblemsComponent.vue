<template>
  <section class="problems" id="problems">
    <img class="problems__background" src="/images/problems/background.png" alt="">
    <div class="problems__container problems__container--top container ">
      <div class="problems__label">
        <svg width="142" height="20" viewBox="0 0 142 20" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd" clip-rule="evenodd"
                d="M6.04034 16.0017L13.1509 13.7456C15.7207 13.0313 18.2135 12.4564 20.8934 11.9468C26.4669 10.8884 32.472 10.3745 38.3538 10.4464C44.1233 10.5182 50.0249 11.1476 55.4597 12.3083C62.5262 13.8174 64.0434 14.7321 70.1718 16.5417C88.9469 22.0796 108.391 20.9581 126.404 13.2186L131.19 10.9472C131.643 10.7164 132.357 10.2591 132.733 10.1262C126.995 12.2408 124.715 13.31 118.36 14.8279C101.199 18.9241 84.4238 17.7743 68.1679 12.3344C65.7853 11.5374 63.5744 10.6271 61.1168 9.86056C44.1519 4.56439 24.8572 6.33486 9.12326 14.3118C8.13012 14.8148 6.82648 15.4333 6.04034 15.9995V16.0017ZM0 16.9446C1.07022 16.3828 2.25054 15.5117 3.38682 14.8257C20.6314 4.40324 42.3969 1.64627 61.8061 8.00516C64.6908 8.95028 67.1902 9.99775 70.0375 10.9625C81.8892 14.9825 95.791 16.4633 109.191 14.6471C117.548 13.5126 127.459 10.6859 134.775 7.02084C136.323 6.24557 140.916 3.96988 141.993 3.08573C140.982 3.40585 139.28 4.31613 138.199 4.80176C122 12.0883 102.791 13.7586 85.4015 9.98686C82.3626 9.32702 79.5241 8.5082 76.6482 7.56962C73.6886 6.60489 71.2971 5.49645 68.4939 4.42284C56.7985 -0.0566902 42.8131 -1.42211 29.6203 1.66152C20.7723 3.72815 13.2808 7.07092 6.26275 11.949C4.92828 12.8767 0.83239 15.8732 0 16.9424L0 16.9446Z"
                fill="#0072B1"/>
        </svg>
      </div>
      <h2 class="problems__title title title--bold">В каких случаях применяют средства для бассейна «АкваДача»?</h2>
    </div>
    <ul class="problems__tabs">
      <li @click="tabId = 0" :class="{active: tabId === 0}">Наполняем бассейн впервые</li>
      <li @click="tabId = 1" :class="{active: tabId === 1}">цветет вода в бассейне</li>
      <li @click="tabId = 2" :class="{active: tabId === 2}">мутная вода в бассейне</li>
      <li @click="tabId = 3" :class="{active: tabId === 3}">дезинфекция</li>
    </ul>
    <div class="problems__container problems__container--bottom container">
      <template v-for="(tab, index) in tabs" :key="index">
        <transition name="fade-tabs" appear mode="out-in">
        <div class="problems__slider slider" v-if="index === tabId">
          <p>{{ tab.text }}</p>
          <div class="slider__content">
            <div class="slider__problem">
              <img :src="tab.imageProblem" alt="">
            </div>
            <div class="slider__decision">
              <ul class="slider__products products"
                  :class="{one: tab.desides.length === 1, two: tab.desides.length === 2, three: tab.desides.length === 3}">
                <template v-for="(item, index) in tab.desides" :key="index">
                  <li class="products__item">
                    <div class="products__image">
                      <img :src="item.image" alt="">
                      <span>{{ item.id }}</span>
                    </div>
                    <div class="products__content">
                      <h3 class="products__title title title--medium">{{ item.title }}</h3>
                      <p>{{ item.description }}</p>
                      <button class="products__link" @click="openPopup(item, 'products')">Подробнее</button>
                    </div>
                  </li>
                </template>
              </ul>
            </div>
            <div class="slider__result">
              <img :src="tab.imageResult" alt=""/>
            </div>
          </div>
        </div>
        </transition>
      </template>
      <div class="problems__label problems__label--bottom">
        <svg width="142" height="20" viewBox="0 0 142 20" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd" clip-rule="evenodd"
                d="M6.04034 16.0017L13.1509 13.7456C15.7207 13.0313 18.2135 12.4564 20.8934 11.9468C26.4669 10.8884 32.472 10.3745 38.3538 10.4464C44.1233 10.5182 50.0249 11.1476 55.4597 12.3083C62.5262 13.8174 64.0434 14.7321 70.1718 16.5417C88.9469 22.0796 108.391 20.9581 126.404 13.2186L131.19 10.9472C131.643 10.7164 132.357 10.2591 132.733 10.1262C126.995 12.2408 124.715 13.31 118.36 14.8279C101.199 18.9241 84.4238 17.7743 68.1679 12.3344C65.7853 11.5374 63.5744 10.6271 61.1168 9.86056C44.1519 4.56439 24.8572 6.33486 9.12326 14.3118C8.13012 14.8148 6.82648 15.4333 6.04034 15.9995V16.0017ZM0 16.9446C1.07022 16.3828 2.25054 15.5117 3.38682 14.8257C20.6314 4.40324 42.3969 1.64627 61.8061 8.00516C64.6908 8.95028 67.1902 9.99775 70.0375 10.9625C81.8892 14.9825 95.791 16.4633 109.191 14.6471C117.548 13.5126 127.459 10.6859 134.775 7.02084C136.323 6.24557 140.916 3.96988 141.993 3.08573C140.982 3.40585 139.28 4.31613 138.199 4.80176C122 12.0883 102.791 13.7586 85.4015 9.98686C82.3626 9.32702 79.5241 8.5082 76.6482 7.56962C73.6886 6.60489 71.2971 5.49645 68.4939 4.42284C56.7985 -0.0566902 42.8131 -1.42211 29.6203 1.66152C20.7723 3.72815 13.2808 7.07092 6.26275 11.949C4.92828 12.8767 0.83239 15.8732 0 16.9424L0 16.9446Z"
                fill="#0072B1"/>
        </svg>
      </div>
    </div>
    <popup-component
      :isOpened="isOpened"
      :dataPopup="dataPopup"
      :isProductPopup="isProductPopup"
      @open-popup="openPopup"
      @close-popup="closePopup"
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
import PopupComponent from '@/components/blocks/PopupComponent'
import SuccessPopup from '@/components/blocks/SuccessPopup'
import RequestPopup from '@/components/blocks/RequestPopup'

export default {
  components: {
    PopupComponent,
    SuccessPopup,
    RequestPopup
  },
  data () {
    return {
      tabId: 1,
      tabs: [
        {
          text: '1 Мутная, зеленая, цветущая вода – главная проблема всех бассейнов на загородных участках нашей планеты. Не успеешь  оглянуться, а вместо прозрачной водички в бассейне  бултыхается какой-то мутный бульон. Есть решение!',
          imageProblem: '/images/problems/pool-1.jpg',
          imageResult: '/images/problems/pool-2.jpg',
          desides: [
            {
              id: 1,
              image: '/images/problems/pic.png',
              title: 'Дезинфицирующее средство',
              description: 'Устраняет зелень, осветляет воду, удаляет известковые отложения, удаляет ржавчину',
              textResult: 'чистый бассейн!',
              benefit: 'Экономичная упаковка - хватит на весь сезон!',
              price: '1500',
              specification: [
                {
                  title: 'Область применения:',
                  text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
                },
                {
                  title: 'Как применять:',
                  text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
                },
                {
                  title: 'Фасовка:',
                  text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
                }
              ]
            }
          ]
        },
        {
          text: '2 Мутная, зеленая, цветущая вода – главная проблема всех бассейнов на загородных участках нашей планеты. Не успеешь  оглянуться, а вместо прозрачной водички в бассейне  бултыхается какой-то мутный бульон. Есть решение!',
          imageProblem: '/images/problems/pool-1.jpg',
          imageResult: '/images/problems/pool-2.jpg',
          desides: [
            {
              id: 1,
              image: '/images/problems/pic.png',
              title: 'Дезинфектор кальций-хлор 92%',
              textResult: 'чистый бассейн!',
              benefit: 'Экономичная упаковка - хватит на весь сезон!',
              price: '1500',
              specification: [
                {
                  title: 'Область применения:',
                  text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
                },
                {
                  title: 'Как применять:',
                  text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
                },
                {
                  title: 'Фасовка:',
                  text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
                }
              ]
            },
            {
              id: 2,
              image: '/images/problems/pic.png',
              title: 'Дезинфицирующее средство',
              textResult: 'чистый бассейн!',
              benefit: 'Экономичная упаковка - хватит на весь сезон!',
              price: '1500',
              specification: [
                {
                  title: 'Область применения:',
                  text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
                },
                {
                  title: 'Как применять:',
                  text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
                },
                {
                  title: 'Фасовка:',
                  text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
                }
              ]
            },
            {
              id: 3,
              image: '/images/problems/pic.png',
              title: 'Активный кислород',
              textResult: 'чистый бассейн!',
              benefit: 'Экономичная упаковка - хватит на весь сезон!',
              price: '1500',
              specification: [
                {
                  title: 'Область применения:',
                  text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
                },
                {
                  title: 'Как применять:',
                  text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
                },
                {
                  title: 'Фасовка:',
                  text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
                }
              ]
            }
          ],
          textResult: 'чистый бассейн!'
        },
        {
          text: '3 Мутная, зеленая, цветущая вода – главная проблема всех бассейнов на загородных участках нашей планеты. Не успеешь  оглянуться, а вместо прозрачной водички в бассейне  бултыхается какой-то мутный бульон. Есть решение!',
          imageProblem: '/images/problems/pool-1.jpg',
          imageResult: '/images/problems/pool-2.jpg',
          desides: [
            {
              id: 1,
              image: '/images/problems/pic.png',
              title: 'Дезинфектор кальций-хлор 92%',
              description: 'Устраняет зелень, осветляет воду, удаляет известковые отложения, удаляет ржавчину',
              textResult: 'чистый бассейн!',
              benefit: 'Экономичная упаковка - хватит на весь сезон!',
              price: '1500',
              specification: [
                {
                  title: 'Область применения:',
                  text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
                },
                {
                  title: 'Как применять:',
                  text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
                },
                {
                  title: 'Фасовка:',
                  text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
                }
              ]
            },
            {
              id: 2,
              image: '/images/problems/pic.png',
              title: 'Дезинфицирующее средство',
              description: 'Устраняет зелень, осветляет воду, удаляет известковые отложения, удаляет ржавчину',
              textResult: 'чистый бассейн!',
              benefit: 'Экономичная упаковка - хватит на весь сезон!',
              price: '1500',
              specification: [
                {
                  title: 'Область применения:',
                  text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
                },
                {
                  title: 'Как применять:',
                  text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
                },
                {
                  title: 'Фасовка:',
                  text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
                }
              ]
            }
          ],
          textResult: 'чистый бассейн!'
        },
        {
          text: '4 Мутная, зеленая, цветущая вода – главная проблема всех бассейнов на загородных участках нашей планеты. Не успеешь  оглянуться, а вместо прозрачной водички в бассейне  бултыхается какой-то мутный бульон. Есть решение!',
          imageProblem: '/images/problems/pool-1.jpg',
          imageResult: '/images/problems/pool-2.jpg',
          desides: [
            {
              id: 1,
              image: '/images/problems/pic.png',
              title: 'Дезинфектор кальций-хлор 92%',
              textResult: 'чистый бассейн!',
              benefit: 'Экономичная упаковка - хватит на весь сезон!',
              price: '1500',
              specification: [
                {
                  title: 'Область применения:',
                  text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
                },
                {
                  title: 'Как применять:',
                  text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
                },
                {
                  title: 'Фасовка:',
                  text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
                }
              ]
            },
            {
              id: 2,
              image: '/images/problems/pic.png',
              title: 'Дезинфицирующее средство',
              textResult: 'чистый бассейн!',
              benefit: 'Экономичная упаковка - хватит на весь сезон!',
              price: '1500',
              specification: [
                {
                  title: 'Область применения:',
                  text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
                },
                {
                  title: 'Как применять:',
                  text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
                },
                {
                  title: 'Фасовка:',
                  text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
                }
              ]
            },
            {
              id: 3,
              image: '/images/problems/pic.png',
              title: 'Активный кислород',
              textResult: 'чистый бассейн!',
              benefit: 'Экономичная упаковка - хватит на весь сезон!',
              price: '1500',
              specification: [
                {
                  title: 'Область применения:',
                  text: 'Быстро и эффективно устраняет помутнение воды дачных бассейнов'
                },
                {
                  title: 'Как применять:',
                  text: 'Разводите коагулянт в ведре с водой. Хорошенько закрытите воду в бассейне'
                },
                {
                  title: 'Фасовка:',
                  text: 'Пакет дойпак со штуцером 28мм, масса - 3 литра. Форма выпуска: водный раствор полиоксихлорида алюминия. Гарантийный срок хранения - 1 год'
                }
              ]
            }
          ],
          textResult: 'чистый бассейн!'
        }
      ],
      isOpened: false,
      dataPopup: {},
      isProductPopup: false,
      isRequestPopup: false,
      isSuccessPopup: false,
      scrollWidth: 0
    }
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
      this.widthScrollBar()
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
      this.isProductPopup = false
      this.isRequestPopup = false
      this.isSuccessPopup = false
      switch (popup) {
        case 'products':
          this.isOpened = true
          this.isProductPopup = true
          break
        case 'request':
          this.isRequestPopup = true
          break
        case 'success':
          this.isSuccessPopup = true
          break
      }
      this.scrollBarVisibility()
    },
    openPopup (data, popup) {
      this.isOpened = false
      this.isProductPopup = false
      this.isRequestPopup = false
      this.isSuccessPopup = false
      switch (popup) {
        case 'products':
          this.isOpened = true
          this.isProductPopup = true
          break
        case 'request':
          this.isRequestPopup = true
          break
        case 'success':
          this.isSuccessPopup = true
          break
      }
      if (data) {
        this.dataPopup = data
      }
      this.scrollBarVisibility()
    }
  }
}
</script>

<style lang="scss" scoped>

.fade-tabs-enter-active {
  animation: opened .5s;
}

.fade-tabs-leave-active {
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

.problems {
  position: relative;
  &__background {
    position: absolute;
    z-index: -1;
    top: 0;
    bottom: 0;
  }
  &__container {
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: none;

    &--top {
      padding-top: 144px;
    }

    &--bottom {
      padding-bottom: 76px;
    }
  }

  &__title {
    margin-top: 48px;
    max-width: 916px;
    color: $accentColor;
    margin-bottom: 44px;
    text-align: center;
  }

  &__tabs {
    height: 80px;
    background-color: $baseColor;
    width: calc(100% + 40px);
    display: grid;
    grid-template-columns: 200px 200px 200px 200px;
    grid-column-gap: 20px;
    align-items: center;
    overflow-y: auto;

    & li {
      font-size: 14px;
      height: 45px;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      width: 100%;
      color: $accentColor;
      cursor: pointer;
      margin: 0 20px;
      text-transform: uppercase;

      &:not(:first-child) {
        border-left: 1px solid #D8D8D8;
      }

      &.active {
        height: 60px;
        background-color: $accentColor;
        color: $baseColor;
        border-radius: 100px;
        border-color: transparent;
        transition: all .5s ease;

        & + li {
          border-color: transparent;
        }
      }
    }
  }

  &__slider {
    padding-top: 32px;
  }

  @media (min-width: $tablet-min) {
    &__container {
      display: flex;
      flex-direction: column;
      align-items: center;

      &--top,
      &--bottom {
        padding: 0 0 76px;
      }
    }
    &__title {
      max-width: 916px;
      color: $accentColor;
      margin-bottom: 40px;
      margin-top: 54px;
      text-align: center;
      letter-spacing: .5px;
    }
    &__tabs {
      border-radius: 100px;
      height: 100px;
      background-color: $baseColor;
      width: 100%;
      display: flex;
      justify-content: space-around;
      align-items: center;
      grid-template-columns: 1fr 1fr 1fr 1fr;
      grid-column-gap: 4px;

      & li {
        height: 45px;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        color: $accentColor;
        cursor: pointer;
        margin: 0 8px;
        padding: 4px;
        text-transform: uppercase;
        font-size: 14px;
        font-family: OpenSansBold;
        letter-spacing: .5px;

        &:not(:first-child) {
          border-left: 1px solid #D8D8D8;
        }

        &.active {
          height: 80px;
          background-color: $accentColor;
          color: $baseColor;
          border-radius: 100px;
          border-color: transparent;
          transition: all .5s ease;

          & + li {
            border-color: transparent;
          }
        }
      }
    }
    &__slider {
      padding-top: 38px;
    }
    &__label {
      &--bottom {
        margin-top: 40px;
      }
    }
  }
  @media (min-width: $desktop) {
    padding-top: 211px;
    &__title {
      margin-bottom: 48px;
      margin-top: 72px;
    }
    &__label {
      &--bottom {
        margin-top: 137px;
      }
    }
    &__tabs {
      padding: 0 42px !important;
      max-width: 1466px;
      margin: 0 auto !important;
      width: 100%;

      & li {
        font-size: 17px;
      }
    }
  }
}

.slider {
  width: 100%;
  max-width: 450px;

  & > p {
    font-size: 16px;
    line-height: 29px;
    color: #565656;
    margin: 0 auto;
    margin-bottom: 24px;
  }

  &__problem,
  &__result,
  &__decision {
    border-radius: 50px;
    overflow: hidden;
    margin-bottom: 20px;

    & img {
      width: 100%;
    }
  }

  &__problem,
  &__result {
    max-height: 200px;
  }

  &__decision {
    background-color: $baseColor;
    padding: 0px 20px;
    box-sizing: content-box;
  }

  &__result {
    margin-bottom: 48px;
  }

  &__label {
    display: flex;
    justify-content: space-around;

    & span {
      display: block;
      left: 50%;
      text-transform: uppercase;
    }
  }

  @media (min-width: $tablet-min) {
    max-width: 1466px;
    &__content {
      display: flex;
      justify-content: center;
      flex-direction: column;
      align-items: center;
    }
    &__problem,
    &__result {
      max-height: 250px;
      width: 60%;

      & img {
        width: 100%;
      }
    }
    &__decision {
      grid-row: 2;
      grid-column: 1/-1;
      width: 60%;
      justify-self: center;
      box-sizing: border-box;
    }
  }
  @media (min-width: $desktop) {
    & > p {
      font-size: 16px;
      line-height: 29px;
      text-align: center;
      color: #565656;
      max-width: 1067px;
      margin: 0 auto 50px;
    }
    &__content {
      border-radius: 60px;
      display: flex;
      justify-content: space-around;
      height: 450px;
      overflow: hidden;
      flex-direction: row;
      align-items: revert;
    }
    &__problem,
    &__result,
    &__decision {
      min-height: 451px;
      position: relative;
      border-radius: 64px 43px;
      overflow: hidden;
      width: 42%;
      transform: skewX(14deg);
      box-shadow: 0px 26px 15px rgba(0, 0, 0, 0.02), 0px 11px 11px rgba(0, 0, 0, 0.03), 0px 3px 6px rgba(0, 0, 0, 0.03), 0px 0px 0px rgba(0, 0, 0, 0.03);
    }
    &__problem,
    &__result {
      & img {
        height: 100%;
        transform: skewX(-14deg);
      }
    }
    &__problem {
      margin-left: -200px;

      & img {
        margin-left: 100px;
      }
    }
    &__result {
      margin-right: -200px;

      & img {
        width: 100%;
        margin-left: -100px;
      }
    }
    &__decision {
      background-color: $baseColor;
      box-sizing: border-box;
      width: 37%;
      padding: 16px 20px;
    }
    &__label {
      display: flex;
      justify-content: space-around;

      & span {
        display: block;
        left: 50%;
        text-transform: uppercase;
      }
    }
  }
}

.products {
  & p {
    font-size: 14px;
    line-height: 25px;
    text-align: left;
    margin-top: 12px;
    margin-bottom: 12px;
  }

  &__item {
    display: flex;
    flex-direction: column;
    width: 100%;
    padding: 16px 0;
  }

  &__image {
    align-self: center;
    position: relative;

    & span {
      position: absolute;
      background-color: $mainColor;
      color: $baseColor;
      border-radius: 50%;
      width: 21px;
      height: 21px;
      top: 7px;
      left: 1px;
      text-align: center;
      font-size: 13px;
    }
  }

  &__content {
    display: flex;
    flex-direction: column;
    margin-top: 16px;
  }

  &__link {
    font-weight: 400;
    font-size: 14px;
    line-height: 22px;
    text-align: center;
    color: $accentColor;
    display: flex;
    align-items: center;
    align-self: flex-end;
    margin-right: 20px;

    &::after {
      content: '\e906';
      font-family: 'icomoon';
      margin-left: 5px;
    }
  }

  &.two,
  &.three {
    & .products__link {
      align-self: flex-start;
      font-size: 14px;
      //font-size: 17px;
    }

    & .products__item {
      flex-direction: row;
      align-items: center;
      padding: 0;
      padding-bottom: 8px;

      &:not(:last-child) {
        border-bottom: 1px solid #dedede;
      }
    }

    & .products__content {
      margin-left: 12px;
      justify-content: space-between;

      & p {
        display: none;
      }
    }

    & .products__image {
      padding-top: 6px;

      & span {
        top: 14px;
      }
    }

    & .products__link {
      margin-top: 12px;
    }
  }

  @media (min-width: $desktop) {
    & p {
      font-size: 14px;
      line-height: 25px;
      text-align: left;
    }
    &__link {
      font-weight: 400;
      font-size: 14px;
      line-height: 22px;
      text-align: center;
      color: $accentColor;
      display: flex;
      align-items: center;

      &::after {
        content: '\e906';
        font-family: 'icomoon';
        margin-left: 5px;
      }
    }
    &.one {
      width: 335px;
      padding-bottom: 41px;
      transform: skewX(-14deg);
      margin-left: 78px;

      & .products__item {
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
      }

      & .products__image {
        height: 267px;

        & img {
          height: 100%;
        }
      }

      & .products__title {
        font-size: 20px;
        line-height: 28px;
        text-align: center;
        letter-spacing: 0.03em;
      }

      & p {
        margin-top: 5px;
        margin-bottom: 14px;
        max-width: 315px;
      }

      & .products__link {
        font-weight: 400;
        font-size: 14px;
        line-height: 22px;
        text-align: center;
        color: $accentColor;
        display: flex;
        align-items: center;

        &::after {
          content: '\e906';
          font-family: 'icomoon';
          margin-left: 5px;
        }
      }
    }
    &.two,
    &.three {
      padding: 61px 38px 61px 20px;
      display: flex;
      flex-direction: column;
      height: 100%;

      & .products__item {
        &:not(:last-child) {
          border-bottom: 1px solid #dedede;
        }

        &:last-child {
          margin-top: 38px;
        }
      }

      & .products__image {
        transform: skewX(-14deg);
        min-width: 140px;
        position: relative;

        & img {
          width: 100%;
        }

        & span {
          position: absolute;
          background-color: $mainColor;
          color: $baseColor;
          border-radius: 50%;
          width: 21px;
          height: 21px;
          top: 14px;
          left: 1px;
          text-align: center;
          font-size: 13px;
        }
      }

      & .products__content {
        transform: skewX(-14deg);
        margin-left: 17px;
        padding-top: 9px;

        & p {
          margin-top: 8px;
          margin-bottom: 8px;
        }

        & h3 {
          font-size: 16px;
          line-height: 22px;
          letter-spacing: 0.03em;
        }
      }
    }
    &.three {
      padding: 9px 22px 31px 35px;;

      & .products__item {
        &:last-child {
          margin-top: 18px;
        }

        &:not(:first-child) {
          margin-top: 20px;
        }

        &:nth-child(2) {
          padding-bottom: 21px;
        }
      }

      & .products__image {
        min-width: 104px;
      }

      & .products__content {
        margin-left: 32px;
        padding-top: 0;
        max-width: 258px;

        & h3 {
          font-size: 20px;
          line-height: 28px;
        }
      }
    }
  }
}
</style>
