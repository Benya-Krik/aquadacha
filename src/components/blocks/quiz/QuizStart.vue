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
            <p>Бонусы после прохождения теста:</p>
            <div class="quiz__form form">
                <p class="checkbox">Советы по уходу за бассейном</p>
                <p class="checkbox">Подбор средств для вашего бассейна</p>
                <div class="form__button-group">
                    <button-default
                        :color="'green'"
                        :text="'Пройти тест'"
                        @click="$emit('toNextStep')"
                    />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import ButtonDefault from '@/components/ui/ButtonDefault.vue'
export default {
  components: {
    ButtonDefault
  }
}
</script>
<style lang="scss">
p.checkbox {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    font-size: 16px;
    line-height: 29px;
    color: #55B03B;
    &::before {
        content: '\e902';
        font-family: 'icomoon';
        background-color: #55B03B;
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
