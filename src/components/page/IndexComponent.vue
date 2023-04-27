<template>
  <main>
    <v-parallax class="parallax first" src="/images/parallax/1.png" />
    <v-parallax class="parallax second" src="/images/parallax/2.png" />
    <v-parallax class="parallax third" src="/images/parallax/3.png" />
    <v-parallax class="parallax forth" src="/images/parallax/4.png" />
    <v-parallax class="parallax fifth" src="/images/parallax/5.png" />
    <main-component v-if="main"/>
    <benefits-component v-if="benefits"/>
    <products-component v-if="products"/>
    <banner-form v-if="banner"/>
    <problems-component v-if="problems"/>
    <banner-instruction v-if="banner2"/>
  </main>
</template>

<script>
import MainComponent from '../index/MainComponent.vue'
import BenefitsComponent from '../index/BenefitsComponent.vue'
import ProductsComponent from '../index/ProductsComponent.vue'
import BannerForm from '../index/BannerForm.vue'
import ProblemsComponent from '../index/ProblemsComponent.vue'
import BannerInstruction from '../index/BannerInstruction.vue'

export default {
  components: {
    MainComponent,
    BenefitsComponent,
    ProductsComponent,
    BannerForm,
    ProblemsComponent,
    BannerInstruction
  },
  data () {
    return {
      main: true,
      benefits: true,
      products: true,
      banner: true,
      problems: true,
      banner2: true
    }
  }
}
</script>

<style lang="scss">

.parallax {
  display: none;
  @media (min-width: 1200px) {
    display: block;
    position: absolute;
    overflow: visible;
  }
}

.first {
  width: 96px;
  top: 153px;
}
.second {
  width: 134px;
  top: 708px;
  right: 0;
}
.third {
  top: 1260px;
  width: 134px;
}
.forth {
  bottom: 1469px;
  width: 126px;
  left: -7px;
}
.fifth {
  right: 0;
  bottom: 969px;
  width: 134px;
}
</style>
