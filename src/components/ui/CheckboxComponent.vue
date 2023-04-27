<template>
  <div class="checkbox">
    <input type="checkbox" :id="id" :name="name"/>
    <label :for="id">{{ text }}</label>
  </div>
</template>

<script>
export default {
  props: ['text', 'id', 'name']
}
</script>

<style lang="scss" scoped>
input {
  display: none;

  &:checked {
    & + label {
      color: $mainColor;

      &::before {
        background-color: $mainColor;
      }
    }
  }
}

label {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  cursor: pointer;
  &::before {
    content: '\e902';
    font-family: 'icomoon';
    background-color: #BBBBBB;
    color: $baseColor;
    margin-right: 8px;
    border-radius: 50%;
    width: 18px;
    height: 18px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 9px;
    padding-top: 2px;
  }
}
</style>
