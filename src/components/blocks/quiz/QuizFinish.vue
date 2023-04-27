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
            <p>Рассчитаем стоимость и перезвоним!</p>
            <form class="quiz__form form" action="" @submit.prevent>
                <div class="form__input-group">
                    <div class="form__top">
                        <div class="input">
                            <radio-button
                              :modificator="'top'"
                                :text="''"
                                :id="'name'"
                            />
                            <input-component
                                :placeholder="'Введите имя'"
                                :modificator="'withRadio'"
                                :radioId="'#name'"
                            />
                        </div>
                        <div class="input">
                            <radio-button
                              :modificator="'top'"
                              :text="''"
                                :id="'number'"
                            />
                            <input-component
                                :placeholder="'Введите телефон'"
                                :modificator="'withRadio'"
                                :radioId="'#number'"
                            />
                        </div>
                    </div>
                    <div class="input">
                        <radio-button
                          :modificator="'top'"
                          :text="''"
                            :id="'massenger'"
                        />
                        <input-component
                            :placeholder="'Где с вами связаться:'"
                            :modificator="'withRadio'"
                            :type="'withContact'"
                            :radioId="'#massenger'"
                        />
                    </div>
                </div>
                <div class="form__button-group">
                    <button-default
                        :color="'blue'"
                        :text="'Отправить'"
                        @click="$emit('closePopup')"
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
  }
}
</script>

<style lang="scss" scoped>
.form {
    &__top {
        margin-bottom: 16px;
    }
    @media (min-width: $tablet-min) {
        &__top {
            display: flex;
            margin-bottom: 16px;
            & + input {
                margin-top: 16px;
            }
        }
        &__button-group {
            display: flex;
            & button + button {
                margin-left: 30px;
            }
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
        margin-top: 16px;
    }
    @media (min-width: $tablet-min) {
        max-height: 64px;
        & + div {
            margin-left: 16px;
        }
    }
    @media (min-width: $desktop) {
        & + div {
            margin-top: 0;
        }
    }
}
</style>
