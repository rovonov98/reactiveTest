<template>
  <div class="forms">
      <form v-if="!isSubmitted" class="forms__container" action="" 
       @submit="submitHandler">
        <div class="form" 
         :class="{ form_completed: firstForm == 'completed', form_active: firstForm == 'active' }">
          <div class="form__head" 
           @click="firstFormChange">
            <div class="form__icon">
              <img class="form__checkmark" src="../assets/img/Vector.svg" alt=""
               v-if="firstForm == 'completed'">
              <span class="form__icon-number"
               v-if="firstForm == 'active'">1</span>
            </div>
            <span class="form__title">Выбор заявителя</span>
          </div>
          <div class="form__body"
           v-if="firstForm == 'active'">
            <label class="form__label label form__label_inactive" 
              :class="{ form__label_active: radio === 'first' }">
             <span class="form__radio-mark label_radio-mark"
             :class="{ radio_checked: radio === 'first' }"></span>
              <input class="form__radio label_input" name="name" type="radio" value="first" v-model="radio">
              <span class="label__description">
                <span class="label__bold-text">Константинопольский К.К.</span>
                <span class="label__text">Физическое лицо</span>
              </span>
            </label>
            <label class="form__label label form__label_inactive"
              :class="{ form__label_active: radio === 'second' }">
              <span class="form__radio-mark label_radio-mark"
              :class="{ radio_checked: radio === 'second' }"></span>
              <input class="form__radio label_input" name="name" type="radio" value="second" v-model="radio">
              <span class="label__description">
                <span class="label__bold-text">ООО &#171;Константинополь&#187;</span>
                <span class="label__text">Юридическое лицо</span>
              </span>
            </label>
            <button type="button" class="form__button button"
             @click="firstFormHandler">Продолжить</button>
          </div>
        </div>
        <div class="form" 
         :class="{ form_completed: secondForm == 'completed', form_active: secondForm == 'active', form_inactive: secondForm == 'inactive' }">
          <div class="form__head"
           @click="secondFormChange">
            <div class="form__icon">
              <img class="form__checkmark" src="../assets/img/Vector.svg" alt=""
               v-if="secondForm == 'completed'">
              <span class="form__icon-number"
               v-if="secondForm != 'completed'">2</span>
            </div>
            <span class="form__title">Данные заявителя</span>
          </div>
          <div class="form__body"
           v-if="secondForm == 'active'">
            <div class="form__input-field">
              <span class="form__input-title">Фамилия</span>
              <input class="input" type="text" placeholder="Константинопольский" 
               v-model="inputs.secondName"
               @input="inputVerification">
            </div>
            <div class="form__input-field">
              <span class="form__input-title">Имя</span>
              <input class="input" type="text" placeholder="Константин" 
               v-model="inputs.firstName"
               @input="inputVerification">
            </div>
            <div class="form__input-field">
              <span class="form__input-title">Отчество</span>
              <input class="input" type="text" placeholder="Константинович" 
               v-model="inputs.thirdName"
               @input="inputVerification">
            </div>
            <div class="form__input-field">
              <span class="form__input-title">Электронная почта</span>
              <input class="input" type="email" placeholder="konstantinopolskiy@mail.ru" 
               v-model="inputs.email"
               @input="inputVerification">
            </div>
            <div class="form__input-field">
              <span class="form__input-title">Телефон</span>
              <input class="input" type="text" placeholder="+7 (901) 123-45-67" 
               v-model="inputs.phoneNumber"
               @input="inputVerification">
            </div>
            <span class="form__document-description">Документ, удостоверяющий личность</span>
            <div class="form__input-field">
              <span class="form__input-title">Документ</span>
              <input class="input" type="text" placeholder="Паспорт" 
               v-model="inputs.passport"
               @input="inputVerification">
            </div>
            <div class="form__series-number">
              <div class="form__input-field form__series-input">
                <span class="form__input-title">Серия</span>
                <input class="input" type="number" placeholder="5700" 
                 v-model="inputs.series"
                 @input="inputVerification">
              </div>
              <div class="form__input-field form__number-input">
                <span class="form__input-title">Номер</span>
                <input class="input" type="number" placeholder="555888" 
                 v-model="inputs.number"
                 @input="inputVerification">
              </div>
            </div>
            <span>Когда выдан</span>
            <div class="form__date">
              <div class="form__input-field form__short-number">
                <span class="form__input-title">День</span>
                <input class="input" type="number" placeholder="19" 
                 v-model="inputs.day"
                 @input="inputVerification">
              </div>
              <div class="form__input-field form__short-number">
                <span class="form__input-title">Месяц</span>
                <input class="input" type="number" placeholder="10" 
                 v-model="inputs.month"
                 @input="inputVerification">
              </div>
              <div class="form__input-field form__average-number">
                <span class="form__input-title">Год</span>
                <input class="input" type="number" placeholder="1990" 
                 v-model="inputs.year"
                 @input="inputVerification">
              </div>
            </div>
            <button type="button" class="form__button button second-button" disabled
             @click="secondFormHandler"
             @mouseenter="inputVerification"
             @touchstart="inputVerification">Продолжить</button>
          </div>
        </div>
        <div class="form" 
         :class="{ form_completed: thirdForm == 'completed', form_active: thirdForm == 'active', form_inactive: thirdForm == 'inactive' }">
          <div class="form__head">
            <div class="form__icon">
              <img class="form__checkmark" src="../assets/img/Vector.svg" alt=""
               v-if="thirdForm == 'completed'">
              <span class="form__icon-number"
               v-if="thirdFormState != 'completed'">3</span>
            </div>
            <span class="form__title">Согласие</span>
          </div>
          <div class="form__body"
           v-if="thirdForm == 'active'">
            <span class="form__consent-requirement">Требуется ваше согласие по следующим пунктам:</span>
            <ul class="form__requirements-list">
              <li><p class="form__requirement">Я подтверждаю, что вся представленная информация является достоверной и точной&#59;</p></li>
              <li><p class="form__requirement">Я несу ответственность в соответствии с действующим законодательством Российской Федерации за предоставление заведомо ложных или неполных сведений&#59;</p></li>
              <li><p class="form__requirement">Я выражаю свое согласие на необходимое использование и обработку своих персональных данных, в том числе в информационных системах&#59;</p></li>
              <li><p class="form__requirement">Со сроками оказания государственной услуги ознакомлен.</p></li>
            </ul>
            <label class="form__label label form__label_inactive checkbox" 
             :class="{ form__label_active: firstCheckbox }">
              <span class="form__checkbox-mark"
               :class="{ checkbox_active: firstCheckbox }">
                <span class="form__inner-checkbox"
                 v-if="{ firstCheckbox }"></span>
              </span>
              <input class="form__checkbox" type="checkbox"
               @change="checkboxVerification"
               v-model="firstCheckbox">
              <span class="label__description">Я подтверждаю свое согласие со всеми вышеперечисленными пунктами</span>
            </label>
            <label class="form__label label form__label_inactive checkbox" 
             :class="{ form__label_active: secondCheckbox }">
              <span class="form__checkbox-mark"
               :class="{ checkbox_active: secondCheckbox }">
                <span class="form__inner-checkbox"
                 v-if="{ secondCheckbox }"></span>
              </span>
              <input class="form__checkbox" type="checkbox"
               @change="checkboxVerification"
               v-model="secondCheckbox">
              <span class="label__description">Я уведомлен о том, что результат будет получен в электронном виде</span>
            </label>
            <div class="form__warning">
              <img class="form__bell bell" src="../assets/img/Bell.svg" alt="Bell">
              <span class="form__warning-text">Пожалуйста, еще раз внимательно проверьте все данные перед отправкой</span>
            </div>
            <button type="submit" class="form__button button third-button" disabled>Отправить</button>
            <span class="form__button-description">
              Нажимая кнопку «Отправить», вы соглашаетесь с <a href="" class="form__button-description-link link">правилами хранения и обработки персональных данных</a>
            </span>
          </div>
        </div>
      </form>
      <div class="form form_completed form_submitted" 
       v-if="isSubmitted">
        <div class="form__head">
          <div class="form__icon">
              <img class="form__checkmark" src="../assets/img/Vector.svg" alt="">
            </div>
          <span class="form__title">Заявление принято</span>
        </div>
        <div class="form__body">
          <p class="form__first-text">
            Номер заявления <span class="form__bold-text">RU-1234567</span>. Максимальный срок предоставления услуги — 20 рабочих дней. Следите за статусом заявления в <a class="link" href="">Личном кабинете</a>.
          </p>
          <p class="form__second-text">Если у вас остались вопросы по оказанию услуги, пожалуйста, обращайтесь по телефону +7 (342) 123-45-67.</p>
          <div class="form__buttons">
            <button class="form__button button button_blue" href="">Вернуться в каталог</button>
            <button class="form__button button button_white" href="">Перейти в личный кабинет</button>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      radio: '',
      firstCheckbox: false,
      secondCheckbox: false,
      isSubmitted: false,
      firstForm: 'active',
      secondForm: 'inactive',
      thirdForm: 'inactive',
      inputs: {
        secondName: '',
        firstName: '',
        thirdName: '',
        email: '',
        phoneNumber: '',
        passport: '',
        series: '',
        number: '',
        day: '',
        month: '',
        year: ''
      }
    }
  },
  methods: {
    submitHandler() {
      this.isSubmitted = !this.isSubmitted
    },
    firstFormHandler() {
      if (this.radio == 'first' || this.radio == 'second') {
        this.firstForm = 'completed'
        if (this.secondForm == 'inactive') {
          this.secondForm = 'active'
        } else {
          this.thirdForm = 'active'
        }
      }
    },
    firstFormChange() {
      if (this.firstForm == 'completed') {
        this.firstForm = 'active'
        this.thirdForm = 'inactive'
        if (this.secondForm == 'active') {
          this.secondForm = 'inactive'
        }
      }
    },
    secondFormChange() {
      if (this.firstForm != 'active') {
        if (this.secondForm == 'completed') {
          this.secondForm = 'active'
          this.thirdForm = 'inactive'
        }
      }
    },
    secondFormHandler() {
      this.secondForm = 'completed'
      this.thirdForm = 'active'
    },
    inputVerification() {
      const button = document.querySelector('.second-button')
      const inputs = Array.from(document.querySelectorAll('input'))
      const isValid = inputs.every((input) => {
        return input.value.length != 0
      })
      if (isValid) {
        button.disabled = false
      } else {
        button.disabled = true
      }
    },
    checkboxVerification() {
      const button = document.querySelector('.third-button')
      if (this.firstCheckbox && this.secondCheckbox) {
        button.disabled = false
      } else {
        button.disabled = true
      }
    }
  }
}
</script>

<style lang="scss">
.forms {
  max-width: $whole-content-width;
  @media(max-width: 576px) {
    max-width: $whole-content-width-mobile;
  }
  margin: 0 auto;
}
.forms__container {
  display: flex;
  flex-direction: column;
}
.form {
  max-width: $main-content-width;
  display: flex;
  flex-direction: column;
  background: $white;
  border-radius: 4px;
  padding: 1rem;
  margin-bottom: 1.2rem;
}
.form_active {
  .form__icon {
    background: $blue;
  }
}
.form_inactive {
  .form__icon {
    background: $grey;
  }
}
.form_completed {
  .form__head {
    cursor: pointer;
  }
  .form__icon {
    background: $green;
  }
  
}
.form__head {
  padding: .9rem 0;
  position: relative;
}
.form__icon {
  position: absolute;
  top: .2rem;
  left: .1rem;
  @include responsive-font(22, 8);
  color: $white;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  width: 2.75rem;
  height: 2.75rem;
  @media(max-width: 768px) {
    top: .6rem;
    left: -.5rem;
    width: 2rem;
    height: 2rem;
  }
}
.form__checkmark {
  max-width: 1.2rem;
}
.form__title {
  margin-left: $form-margin;
  @include responsive-font(21, 10);
  font-weight: 700;
}
.form__body {
  display: flex;
  flex-direction: column;
  max-width: $form-content-width;
  @media(max-width: 576px) {
    max-width: $form-content-width-mobile;
  }
  margin-left: $form-margin;
}
.form_submitted {
  .form__body {
    max-width: $form-submitted-width;
  }
}
.label {
  position: relative;
  display: flex;
  padding: 1rem;
  margin-bottom: 1rem;
  border-radius: 4px;
  cursor: pointer;
}
.label_radio-mark {
  position: absolute;
  top: 1rem;
  left: 1.2rem;
  height: 1rem;
  width: 1rem;
  border: 2px solid $dark-grey;
  border-radius: 50%;
}
.form__checkbox {
  display: none;
}
.form__checkbox-mark {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  top: 1rem;
  left: 1.2rem;
  height: 1rem;
  width: 1rem;
  border: 2px solid $dark-grey;
  border-radius: 1px;
}
.checkbox_active {
  background: $blue;
  border: none;
}
.form__inner-checkbox {
  width: .3rem;
  height: .6rem;
  border-bottom: 2px solid $white;
  border-right: 2px solid $white;
  transform: rotate(45deg);
}
.radio_checked {
  border: .3rem solid $blue;
}
.label_input {
  display: none;
}
.label__description {
  display: flex;
  flex-direction: column;
  margin-left: 2rem;
}
.label__bold-text {
  font-weight: 700;
}
.label__text {
  font-weight: 400;
}
.form__label_inactive {
  background: $light-grey;
}
.form__label_active {
  box-shadow: inset 0px 0px 0px 2px $blue;
  background: $white;
}
.form__input-field {
  display: flex;
  flex-direction: column;
  margin-bottom: .9rem;
}
.form__series-input {
  max-width: $series-input;
}
.form__number-input {
  max-width: $number-input;
}
.form__series-number {
  display: flex;
  justify-content: space-between;
}
.form__date {
  display: flex;
  justify-content: space-between;
  color: #848E99;
}
.form__short-number {
  max-width: $short-input;
}
.form__average-number {
  max-width: $average-input;
}
.form__document-description {
  margin-bottom: 1rem;
  font-weight: 600;
}
.form__input-title {
  margin-bottom: .5rem;
}
.form__consent-requirement {
  font-weight: 600;
}
.form__warning {
  padding: .9rem 3rem 1.2rem .9rem;
  margin-bottom: .9rem;
  background: $light-yellow;
  display: flex;
  align-items: baseline;
}
.form__warning-text {
  margin-left: .6rem;
}
.bell {
  max-width: 1.3rem;
}
.form__requirements-list {
  margin-left: $form-li-margin;
  margin-bottom: 1.3rem;
}
.form__requirement {
  margin-top: .4rem;
}
.form__button-description {
  @include responsive-font(14, 8);
  margin-top: .9rem;
}
.link {
  color: $light-blue;
  text-decoration: none;
}
.input {
  padding: .65rem;
  @include responsive-font(18, 9);
  font-weight: 400;
  outline: none; 
  border: 1px solid $transparent-grey;
  border-radius: 4px;
}
.form__first-text {
  margin-bottom: 2rem;
}
.form__second-text {
  margin-bottom: 1.5rem;
}
.form__bold-text {
  font-weight: 600;
}
.form__buttons {
  display: flex;
  justify-content: space-between;
}
.button {
  background: $blue;
  padding: .8rem 0;
  font-weight: 400;
  color: $white;
  border-radius: 4px;
  border: none;
  @include responsive-font(18, 9);
  cursor: pointer;
}
.button_white {
  background: $white;
  border: 1px solid $lighter-blue;
  padding: .75rem .5rem;
  color: $dark-blue;
}
.button_blue {
  padding: .75rem 2rem;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>