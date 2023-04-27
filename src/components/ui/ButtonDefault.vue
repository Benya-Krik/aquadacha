<template>
  <button class="button" :class="`button--${color} button--${svg}`">
    {{ text }}
  </button>
</template>

<script>
export default {
  props: ['text', 'svg', 'color']
}
</script>

<style lang="scss" scoped>
.button {
  color: $baseColor;
  border-radius: 100px;
  font-weight: 400;
  font-size: 16px;
  line-height: 26px;
  text-align: center;
  height: 63px;
  width: 100%;
  transition: all .5s ease;
  opacity: 1;

  &--green {
    background-color: $mainColor;

    &:hover {
      background-color: #1A931F;
    }
  }

  &--blue {
    background-color: $accentColor;
    border: 1px solid $accentColor;

    &:hover {
      background-color: $baseColor;
      color: $accentColor;
    }
  }

  &--transparent {
    background-color: transparent;
    border: 1px solid transparent;
    color: #BBBBBB;
    box-sizing: border-box;
    max-width: 200px;

    &:hover {
      border-color: #BBBBBB;
    }
  }

  &--arrow {
    &::after {
      content: '\e906';
      font-family: 'icomoon';
      margin-left: 8px;
      font-size: 15px;
    }
  }

  &--phone {
    &::before {
      content: '\e903';
      font-family: 'icomoon';
      font-size: 12px;
      margin-right: 12px;
    }
  }

  &--back {
    &::before {
      content: '\e901';
      font-family: 'icomoon';
      font-size: 12px;
      margin-right: 18px;
    }
  }

  &--next {
    &::after {
      content: '\e906';
      font-family: 'icomoon';
      font-size: 12px;
      margin-left: 18px;
    }
  }

  @media (min-width: $tablet-min) {
    height: 56px;
  }
  @media (min-width: $desktop) {
    height: 70px;
  }
}
</style>
