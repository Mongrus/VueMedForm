<template>
  <div class="main">
    <h2>
      <img src="https://1409hospital.ru/assets/images/mbr-4.png" alt="" />
      Заполните пожалуйста анкету
      <img src="https://1409hospital.ru/assets/images/mbr-4.png" alt="" />
    </h2>
    <h4>
      Поля помеченные <span>*</span> являются обязательными для заполнения
    </h4>
    <form @submit.prevent="submitForm">
      <div class="block">
        <h3>Общая информация:</h3>
        <div class="inputDiv">
          <label for="surname">Фамилия<span>*</span></label>
          <input
            type="text"
            id="surname"
            v-model="state.surname"
            placeholder="Иванов"
          />
          <p v-if="v$.surname.$error">Фамилия обязательна</p>
        </div>
        <div class="inputDiv">
          <label for="name">Имя<span>*</span></label>
          <input
            type="text"
            id="name"
            v-model="state.name"
            placeholder="Иван"
          />
          <p v-if="v$.name.$error">Имя обязательно</p>
        </div>
        <div class="inputDiv">
          <label for="patronymic">Отчество</label>
          <input
            type="text"
            id="patronymic"
            v-model="state.patronymic"
            placeholder="Иванович"
          />
        </div>
        <div class="inputDiv">
          <label for="birthDate">Дата рождения<span>*</span></label>
          <input type="date" id="birthDate" v-model="state.birthDate" />
          <p v-if="v$.birthDate.$error">Дата рождения обязательна</p>
        </div>
        <div class="inputDiv">
          <label for="phone">Номер телефона<span>*</span></label>
          <input
            type="tel"
            v-model="state.phone"
            id="phone"
            maxlength="11"
            pattern="^7\d{10}$"
            title="Номер телефона должен начинаться с 7 и содержать 11 цифр"
            placeholder="79377567700"
          />
          <p v-if="v$.phone.$error">Номер телефона обязателен</p>
        </div>
        <div class="inputDiv">
          <label for="gender">Пол</label>
          <select id="gender" v-model="state.gender">
            <option value="" disabled>Выберите пол</option>
            <option value="male">Мужской</option>
            <option value="female">Женский</option>
          </select>
        </div>
        <div class="inputDiv clientGroup">
          <label for="clientGroup">Группа клиентов<span>*</span></label>
          <select id="clientGroup" v-model="state.clientGroup" multiple>
            <option value="VIP">VIP</option>
            <option value="Problematic">Проблемные</option>
            <option value="OMS">ОМС</option>
          </select>
          <p v-if="v$.clientGroup.$error">Группа клиентов обязательна</p>
        </div>
        <div class="inputDiv">
          <label for="doctor">Лечащий врач</label>
          <select id="doctor" v-model="state.doctor">
            <option value="" disabled>Выберите врача</option>
            <option value="Ivanov">Иванов</option>
            <option value="Zakharov">Захаров</option>
            <option value="Chernysheva">Чернышева</option>
          </select>
        </div>
        <div class="inputDiv sms">
          <label for="noSMS">Не отправлять СМС</label>
          <input id="noSMS" v-model="state.noSMS" type="checkbox" />
        </div>
      </div>
      <div class="block">
        <h3>Адрес проживания:</h3>
        <div class="inputDiv">
          <label for="index">Индекс</label>
          <input
            type="number"
            id="index"
            v-model="state.index"
            placeholder="Индекс"
          />
        </div>
        <div class="inputDiv">
          <label for="country">Страна</label>
          <input id="country" v-model="state.country" placeholder="Страна" />
        </div>
        <div class="inputDiv">
          <label for="region">Область</label>
          <input id="region" v-model="state.region" placeholder="Область" />
        </div>
        <div class="inputDiv">
          <label for="city">Город<span>*</span></label>
          <input id="city" v-model="state.city" placeholder="Город" />
          <p v-if="v$.city.$error">Указывать город обязательно</p>
        </div>
        <div class="inputDiv">
          <label for="street">Улица</label>
          <input id="street" v-model="state.street" placeholder="Улица" />
        </div>
        <div class="inputDiv">
          <label for="house">Дом</label>
          <input id="house" v-model="state.house" placeholder="Дом" />
        </div>
        <button type="submit">Отправить 👨🏻‍⚕️</button>
      </div>
      <div class="block">
        <h3>Документ подтверждающий личность:</h3>
        <div class="inputDiv">
          <label for="docType">Тип документа<span>*</span></label>
          <select id="docType" v-model="state.docType">
            <option value="" disabled>Выберите тип документа</option>
            <option value="Passport">Паспорт</option>
            <option value="BirthCertificate">Свидетельство о рождении</option>
            <option value="WaterCertificate">Вод. удостоверение</option>
          </select>
          <p v-if="v$.docType.$error">Тип документа обязателен</p>
        </div>
        <div class="inputDiv">
          <label for="docSeries">Серия</label>
          <input
            type="number"
            id="docSeries"
            v-model="state.docSeries"
            placeholder="Серия"
          />
        </div>
        <div class="inputDiv">
          <label for="docNumber">Номер</label>
          <input
            type="number"
            id="docNumber"
            v-model="state.docNumber"
            placeholder="Номер"
          />
        </div>
        <div class="inputDiv">
          <label for="docIssuedBy">Кем выдан</label>
          <input
            id="docIssuedBy"
            v-model="state.docIssuedBy"
            placeholder="Кем выдан"
          />
          <label for="docIssueDate">Дата выдачи<span>*</span></label>
          <input id="docIssueDate" v-model="state.docIssueDate" type="date" />
          <p v-if="v$.docIssueDate.$error">Дата выдачи обязательна</p>
        </div>
      </div>
      <div class="btnDiv notes">
        <h5 v-if="state.surname || state.name">
          {{ state.surname }} {{ state.name }}
        </h5>
        <h5 v-if="state.birthDate">Дата рождения {{ state.birthDate }}</h5>
        <h5 v-if="state.phone">т. {{ state.phone }}</h5>
        <h5 v-if="state.city">Из города {{ state.city }}</h5>
        <h2 v-if="state.sent">Отправлено</h2>
      </div>
    </form>
  </div>
</template>

<script>
import { reactive, computed } from 'vue';
import { useVuelidate } from '@vuelidate/core';
import { required, helpers } from '@vuelidate/validators';

// const { minLength, maxLength, pattern } = helpers;

export default {
  setup() {
    const state = reactive({
      surname: '',
      name: '',
      patronymic: '',
      birthDate: '',
      phone: '',
      gender: '',
      clientGroup: [],
      doctor: '',
      noSMS: false,
      index: '',
      country: '',
      region: '',
      city: '',
      street: '',
      house: '',
      docType: '',
      docSeries: '',
      docNumber: '',
      docIssuedBy: '',
      docIssueDate: '',
      sent: false,
    });

    const rules = computed(() => ({
      surname: { required },
      name: { required },
      birthDate: { required },
      phone: { required, pattern: /^7\d{10}$/ },
      clientGroup: { required },
      city: { required },
      docType: { required },
      docIssueDate: { required },
      // Дополнительные правила валидации
    }));

    const v$ = useVuelidate(rules, state);

    function submitForm() {
      v$.value.$touch();
      if (v$.value.$invalid) {
        return;
      }
      this.state.sent = true;
      console.log(this.state);
    }

    return { state, v$, submitForm };
  },
};
</script>

<style lang="sass" scoped>
// Шрифты
@import url('https://fonts.googleapis.com/css2?family=Bad+Script&display=swap')

// Миксины
@mixin respond($breakpoint)
    @if $breakpoint == phone
        @media only screen and (max-width: 700px)
            @content

    @if $breakpoint == tab-port
        @media only screen and (max-width: 900px)
            @content

    @if $breakpoint == tab-land
        @media only screen and (max-width: 1070px)
            @content

    @if $breakpoint == tab-pc
        @media only screen and (max-width: 1220px)
            @content

    @if $breakpoint == big-screen
        @media only screen and (min-width: 1800px)
            @content

.main
  margin: 5rem 0
  background: rgba(255, 255, 255, 0.2)
  border-radius: 1.5rem
  box-shadow: 4rem 4rem 30rem rgba(0, 0, 0, .5)
  backdrop-filter: blur(5px)
  -webkit-backdrop-filter: blur(5px)
  border: 1px solid rgba(255, 255, 255, 0.3)
  width: 75rem
  font-size: 1.5rem
  padding: 2rem 3rem 8rem 3rem
  form
    display: flex
    flex-wrap: wrap
    justify-content: space-around
    @include respond(phone)
      flex-wrap: nowrap
      flex-direction: column
      align-items: center
  h2
    padding-bottom: 1.8rem
    text-align: center
    font-size: 3rem
    border-bottom: 1px solid rgba(255, 255, 255, 0.3)
    img
      transform: translateY(.5rem)
      width: 3rem

  h3
    padding-bottom: .5rem
  h4
    padding: 1rem 3.5rem
    font-size: 1.6rem
    border-bottom: 1px solid rgba(255, 255, 255, 0.3)
    text-decoration: underline
  span
    color: Crimson
  button
    transform: translate(7rem, 4rem)
    width: 15rem
    height: 4rem
    border: none
    background-color: SteelBlue
    font-size: 2rem
    color: white
    border-radius: 1rem
    cursor: pointer
    &:hover
      transform: translate(7rem, 3.3rem)
      box-shadow: 1rem .7rem .1rem black
      transition: .3s
    &:not(nover)
      transition: .3s
    &:active
      transform: translate(7rem, 3.7rem)
      transition: .1s

.block
 display: flex
 flex-direction: column
 padding: 2rem 0 0 0

.inputDiv
  display: flex
  flex-direction: column
  margin-bottom: 1rem
  label
    font-size: 1.6rem
    padding-bottom: .1rem
  input
    width: 30rem
    height: 2rem
    font-size: 1.5rem
  select
    width: 100%
    height: 2rem
    font-size: 1.5rem
  p
    color: DarkBlue
    background-color: #8EC5FC
    background-image: linear-gradient(62deg, #8EC5FC 0%, #E0C3FC 100%)
    border-radius: 0 0 1rem 1rem
    text-align: center

.clientGroup
  select
    width: 100%
    height: 6rem
    text-align: center
    font-size: 1.5rem
    padding-top: .3rem

.sms
  display: flex
  flex-direction: column
  input
    width: 1.7rem
    margin: .3rem 0 1rem 0


.btnDiv
  display: flex
  justify-content: center
  align-items: center
  flex-direction: column
  width: 30rem
  h5
    font-family: "Bad Script", cursive
    color: DarkBlue
    font-size: 2rem

.notes
  background: center url('https://aigis.club/uploads/posts/2022-01/1642155415_51-adonius-club-p-fon-dlya-zametok-53.png')
  background-repeat: no-repeat
  background-size: 100%
  h2
    font-size: 4rem
    transform: rotate(40deg)
    color: DarkBlue
    border: .3rem solid DarkBlue
    padding: 1rem
    position: absolute
</style>
