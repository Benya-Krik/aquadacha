<template>
  <button class="button button--play">
    <svg width="66" height="66" viewBox="0 0 66 66" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path fill-rule="evenodd" clip-rule="evenodd"
            d="M61.4087 16.3565C52.2261 0.573911 32.1391 -4.87826 16.3565 4.30435C0.573911 13.487 -4.87826 33.5739 4.30435 49.3565C13.487 65.1391 33.5739 70.5913 49.3565 61.4087C65.1391 52.2261 70.5913 32.1391 61.4087 16.3565ZM46.2 55.6696C33.5739 62.8435 17.5043 58.5391 10.3304 45.913C3.15652 33.287 7.46087 17.2174 20.087 10.0435C32.713 2.86956 48.7826 7.17391 55.9565 19.8C63.1304 32.4261 58.8261 48.4957 46.2 55.6696ZM44.7652 31.5652L27.5478 21.5217C26.113 20.6609 24.6783 21.2348 24.6783 23.2435V43.3304C24.6783 45.0522 26.113 45.913 27.5478 45.0522L44.7652 35.2957C46.2 34.4348 46.2 33 44.7652 31.8522V31.5652Z"
            fill="#4EAB36"/>
      <defs>
        <linearGradient id="paint0_linear_2_126" x1="12.0522" y1="12.3391" x2="68.5826" y2="74.3217"
                        gradientUnits="userSpaceOnUse">
          <stop stop-color="#4EAB36"/>
          <stop offset="1" stop-color="#219322"/>
        </linearGradient>
      </defs>
    </svg>
  </button>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.button {
  &--play {
    filter: drop-shadow(0px 29px 12px rgba(0, 0, 0, 0.01)) drop-shadow(0px 16px 10px rgba(0, 0, 0, 0.05)) drop-shadow(0px 7px 7px rgba(0, 0, 0, 0.09)) drop-shadow(0px 2px 4px rgba(0, 0, 0, 0.1)) drop-shadow(0px 0px 0px rgba(0, 0, 0, 0.1));
    & path {
      transition: .5s ease;
    }
    &:hover {
      & path {
        transition: .5s ease;
        fill: #1A931F;
      }
    }
  }
}
</style>
