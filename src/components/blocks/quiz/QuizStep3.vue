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
            <p>3. Какая проблема в бассейне вас беспокоит?</p>
            <form class="quiz__form form" action="" @submit.prevent>
                <div class="form__input-group">
                    <div class="form__left">
                        <checkbox-component
                            :text="'Цветет вода'"
                            :id="'color'"
                            :name="'problem'"
                        />
                        <checkbox-component
                            :text="'Уровень pH не в норме'"
                            :id="'level'"
                            :name="'problem'"
                        />
                        <checkbox-component
                            :text="'Нужна дезинфекция'"
                            :id="'desinfection'"
                            :name="'problem'"
                        />
                    </div>
                    <div class="form__right">
                        <checkbox-component
                            :text="'Мутная вода'"
                            :id="'muddy'"
                            :name="'problem'"
                        />
                        <checkbox-component
                            :text="'Ржавчина'"
                            :id="'rust'"
                            :name="'problem'"
                        />
                    </div>
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
import CheckboxComponent from '@/components/ui/CheckboxComponent.vue'
export default {
  components: {
    ButtonDefault,
    CheckboxComponent
  }
}
</script>

<style lang="scss" scoped>
.form {
    &__input-group {
        & div + div.checkbox {
            margin-top: 16px;
            margin-bottom: 0;
        }
    }
    &__left {
        margin-bottom: 16px;
    }
    @media (min-width: $tablet-min) {
        &__input-group {
            display: flex;
        }
        &__left {
            margin-right: 40px;
            margin-bottom: 0;
        }
    }
}
</style>
