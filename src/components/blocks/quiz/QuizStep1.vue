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
            <p>1. Какого типа ваш бассейн?</p>
            <form class="quiz__form form" action="" @submit.prevent>
                <radio-button
                    :id="'advice'"
                    :text="'Надувной / Каркасный'"
                    class="form__radio"
                />
                <radio-button
                    :id="'selection'"
                    :text="'Вкапываемый'"
                    class="form__radio"
                />
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
import RadioButton from '../../ui/RadioButton.vue'
export default {
  components: {
    RadioButton,
    ButtonDefault
  }
}
</script>

<style lang="scss" scoped>
.form {
    & label {
        line-height: 29px;
    }
}
</style>
