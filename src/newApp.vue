<template>
  <form>
    <div class="generalInfo">
      <h2>Общая информация:</h2>
      <label>Фамилия</label>
      <input type="text" placeholder="Иванов" />
      <label>Имя</label>
      <input type="text" placeholder="Иван" />
      <label>Отчество</label>
      <input type="text" placeholder="Иванович" />
      <input type="date" />
      <label>Номер телефона в формате - 79370989922</label>
      <input
        type="tel"
        maxlength="11"
        pattern="^7\d{10}$"
        title="Номер телефона должен начинаться с 7 и содержать 11 цифр"
      />
      <label>Пол</label>
      <select>
        <option value="">Выберите пол</option>
        <option value="male">Мужской</option>
        <option value="female">Женский</option>
      </select>
      <label>Группа клиентов</label>
      <select multiple>
        <option value="VIP">VIP</option>
        <option value="Problematic">Проблемные</option>
        <option value="OMS">ОМС</option>
      </select>
      <label for="doctor">Лечащий врач</label>
      <select id="doctor" v-model="doctor">
        <option value="Ivanov">Иванов</option>
        <option value="Zakharov">Захаров</option>
        <option value="Chernysheva">Чернышева</option>
      </select>
      <label for="noSMS">Не отправлять СМС</label>
      <input id="noSMS" v-model="noSMS" type="checkbox" />
    </div>
    <div class="generalInfo">
      <h2>Адрес:</h2>

      <label for="index">Индекс</label>
      <input id="index" v-model="index" placeholder="Индекс" />

      <label for="country">Страна</label>
      <input id="country" v-model="country" placeholder="Страна" />

      <label for="region">Область</label>
      <input id="region" v-model="region" placeholder="Область" />

      <label for="city">Город*</label>
      <input id="city" v-model="city" placeholder="Город" />

      <label for="street">Улица</label>
      <input id="street" v-model="street" placeholder="Улица" />

      <label for="house">Дом</label>
      <input id="house" v-model="house" placeholder="Дом" />
    </div>
    <div class="generalInfo">
      <h2>Документ:</h2>
      <label for="docType">Тип документа</label>
      <select id="docType" v-model="docType">
        <option value="Passport">Паспорт</option>
        <option value="BirthCertificate">Свидетельство о рождении</option>
        <option value="WaterCertificate">Вод. удостоверение</option>
      </select>
      <label for="docSeries">Серия</label>
      <input id="docSeries" v-model="docSeries" placeholder="Серия" />
      <label for="docNumber">Номер</label>
      <input id="docNumber" v-model="docNumber" placeholder="Номер" />
      <label for="docIssuedBy">Кем выдан</label>
      <input id="docIssuedBy" v-model="docIssuedBy" placeholder="Кем выдан" />
      <label for="docIssueDate">Дата выдачи</label>
      <input id="docIssueDate" v-model="docIssueDate" type="date" />
    </div>

    <button type="submit">Отправить</button>
  </form>
</template>

<script>
import { reactive, computed } from 'vue';
import { useVuelidate } from '@vuelidate/core';
import { required, email } from '@vuelidate/validators';
</script>

<style lang="sass" scoped>
.generalInfo
  display: flex
  flex-direction: column

.selectedV
  color: red
</style>
