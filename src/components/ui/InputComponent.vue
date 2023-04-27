<template>
  <div>
    <input class="input" :class="`input--${modificator} input--${type}`" :placeholder="placeholder" @focus="isChecked(radioId)"/>
    <div class="input__social" :class="`input__social--${type}`" v-if="type">
      <span class="phone"></span>
      <span class="whatsapp"></span>
      <span class="telegram"></span>
    </div>
  </div>
</template>

<script>
export default {
  props: ['placeholder', 'modificator', 'radioId', 'type'],
  methods: {
    isChecked (id) {
      document.querySelector(id).checked = true
    }
  }
}
</script>

<style lang="scss" scoped>
.input {
  border: 1px solid #D9D9D9;
  border-radius: 100px;
  padding: 24px 20px 24px 38px;
  max-height: 70px;
  width: 100%;
  outline: none;
  position: relative;
  &__social {
    position: absolute;
    right: 20px;
    top: 47%;
    width: 100px;
    height: 30px;
    transform: translateY(-50%);
    display: flex;
    justify-content: space-between;
    align-items: center;
    & span {
      min-width: 32px;
      min-height: 32px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      &:not(:last-child) {
        margin-right: 6px;
      }
      &::before {
        color: $baseColor;
      }
      &.whatsapp {
        background-color: #4CAF50;
        font-size: 18px;
      }
      &.telegram {
        background-color: #2197D5;
        font-size: 15px;
      }
      &.phone {
        background-color: #0072B1;
        &::before {
          content: '\e903';
          font-family: 'icomoon';
          font-size: 12px;
        }
      }
    }
  }
  &::placeholder {
    color: #BBBBBB;
    font-size: 16px;
    line-height: 22px;
  }

  &--withRadio {
    padding-left: 60px;
    max-height: 64px;
    cursor: pointer;
  }
  &--withContact {
  }
}
</style>
