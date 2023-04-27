<template>
    <div class="quiz">
        <div class="quiz__background">
            <img src="\images\popup\background.png" alt="">
            <div class="quiz__text">
                <h3 class="quiz__title title title--medium">Ответьте <span class="green">на 5 вопросов!</span></h3>
                <p>и уже через 15 минут наш менеджер рассчитает и сообщит вам стоимость</p>
            </div>
        </div>
        <div class="quiz__content">
            <h2 class="quiz__title title title--bold">Подберем идеальное средство для чистой воды в бассейне!</h2>
            <p>2. Какого объема ваш бассейн?</p>
            <form class="quiz__form form" action="" @submit.prevent>
                <div class="form__input-group">
                    <div class="input">
                        <radio-button
                            :text="''"
                            :id="'volume'"
                        />
                        <input-component
                            :placeholder="'Введите объем'"
                            :modificator="'withRadio'"
                            :radioId="'#volume'"
                        />
                    </div>
                    <radio-button
                        :text="'Не знаю'"
                        :id="'dont'"
                    />
                </div>
                <div class="form__button-group">
                    <button-default
                        :color="'green'"
                        :text="'Далее'"
                        :svg="'next'"
                        @click="$emit('toNextStep')"
                    />
                    <button-default
                        :color="'transparent'"
                        :text="'Назад'"
                        :svg="'back'"
                        @click="$emit('back')"
                    />
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import ButtonDefault from '@/components/ui/ButtonDefault.vue'
import InputComponent from '@/components/ui/InputComponent.vue'
import RadioButton from '@/components/ui/RadioButton.vue'
export default {
  components: {
    ButtonDefault,
    InputComponent,
    RadioButton
  },
  data () {
    return {
      test: ''
    }
  }
}
</script>

<style lang="scss" scoped>
.form {
    &__input-group {
        display: flex;
        flex-direction: column;
        align-items: baseline;
    }
    @media (min-width: $desktop) {
        &__input-group {
            flex-direction: row;
        }
    }
}

.input {
    position: relative;
    .radio {
        position: absolute;
        left: 28px;
        top: 50%;
        transform: translateY(-50%);
        z-index: 10;
    }
    & + div {
        margin-top: 24px;
        margin-left: 28px;
    }
    @media (min-width: $desktop) {
        & + div {
            margin-left: 40px;
        }
    }
}

</style>
