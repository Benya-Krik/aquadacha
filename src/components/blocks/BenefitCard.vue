<template>
  <div class="benefit">
    <div class="circle">
      <svg width="104" height="33" viewBox="0 0 104 33" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path
          d="M0.981807 31.5003L1 32.5H104V32V31.5C92.8248 31.5 87.7757 24.6627 82.3166 17.2703C82.0545 16.9153 81.7913 16.559 81.5266 16.2021C78.6515 12.327 75.579 8.39217 71.3817 5.43501C67.1693 2.46719 61.8492 0.5 54.5 0.5C46.7845 0.5 41.1891 2.40196 36.7284 5.28828C32.2812 8.16585 28.9883 12.0065 25.8632 15.8213C25.6018 16.1404 25.3416 16.4593 25.0819 16.7776C19.1162 24.0878 13.4371 31.0468 0.981807 31.5003Z"
          fill="white" stroke="#ECECEC"/>
        <rect x="1" y="32" width="103" height="1" fill="white"/>
      </svg>
    </div>
    <h3 class="benefit__title title title--medium">{{ title }}</h3>
    <p>{{ text }}</p>
  </div>
</template>

<script>
export default {
  props: ['text', 'title']
}
</script>

<style lang="scss" scoped>
.benefit {
  padding: 16px;
  background-color: $baseColor;
  border: 1px solid #ECECEC;
  border-radius: 10px;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  text-align: center;

  &__title {
    text-transform: uppercase;
  }

  & p {
    font-size: 14px;
    line-height: 21px;
    color: #565656;
  }

  @media (min-width: $tablet-min) {
    align-items: center;
    position: relative;
    padding: 10px 4px 4px;
    &__title {
      font-size: 16px;
      margin-bottom: 8px;
    }
    &::before {
      content: '\e902';
      font-family: 'icomoon';
      background-color: $mainColor;
      color: $baseColor;
      border-radius: 50%;
      width: 22px;
      height: 22px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 12px;
      position: absolute;
      top: -9px;
      left: 50%;
      transform: translate(-40%, -50%);
      z-index: 100;
    }
  }
  @media (min-width: $desktop) {
    padding: 20px 12px 20px;
    &__title {
      font-size: 18px;
    }
    &::before {
      width: 26px;
      height: 26px;
      font-size: 14px;

    }
  }
  @media (min-width: 1400px) {
    padding: 25px 26px 27px;
  }
}

.circle {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translate(-50%, -81%);
}
</style>
