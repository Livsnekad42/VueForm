<template>
  <div id="form-outer">
    <p id="description">
      Форма создания клиента
    </p>
    <form id="client-form" @submit.prevent="submit">
      <fieldset>
        <p>Основные данные</p>
        <div class="rowTab">
          <div class="labels">
            <label id="surname-label" for="surname">* Фамилия: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="surname" id="surname" class="input-field" placeholder="Введите фамилию" v-model.trim="$v.surname.$model">
            <span v-if="!$v.surname.required && $v.surname.$dirty">Введите фамилию</span>
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="name-label" for="name">* Имя: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="name" id="name" class="input-field" placeholder="Введите имя" v-model.trim="$v.name.$model">
            <span v-if="!$v.name.required && $v.name.$dirty">Введите имя</span>
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="patronym-label" for="patronym">Отчество: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="patronym" id="patronym" class="input-field" placeholder="Отчество">
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="birthdate-label" for="birthdate">Дата рождения: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="birthdate" id="birthdate" class="input-field" placeholder="Дата рождения" v-model.trim="$v.birthdate.$model">
            <span v-if="!$v.birthdate.required && $v.birthdate.$dirty">Введите дату в формате DD-MM-YYYY</span>
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="phone-label" for="phone">Номер телефона: </label>
          </div>
          <div class="rightTab">
            <input type="tel" name="phone" id="phone" class="input-field" placeholder="Номер телефона" v-model="$v.phone.$model">
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="sex-label" for="sex">Пол: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="sex" id="sex" class="input-field" placeholder="Пол">
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label for="clientGroup">Группа клиентов</label>
          </div>
          <div class="rightTab">
            <select id="clientGroup" name="clientGroup" class="multiselect" multiple v-model.trim="$v.clientGroup.$model">
              <option value="VIP">VIP</option>
              <option value="trouble">Проблемные</option>
              <option value="OMS">ОМС</option>
            </select>
            <span v-if="!$v.clientGroup.required && $v.clientGroup.$dirty">Выберите группу клиента</span>
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label for="leadDoctor">Лечащий врач</label>
          </div>
          <div class="rightTab">
            <select id="leadDoctor" name="leadDoctor" class="dropdown">
              <option disabled selected value>Выберите врача</option>
              <option value="Иванов">Иванов</option>
              <option value="Захаров">Захаров</option>
              <option value="Чернышева">Чернышева</option>
            </select>
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label for="notifications">Не отправлять СМС</label>
          </div>
          <div class="rightTab">
            <input type="checkbox" id="notifications" name="notifications">
          </div>
        </div>
      </fieldset>

      <fieldset>
        <p>Адрес</p>
        <div class="rowTab">
          <div class="labels">
            <label id="zipcode-label" for="zipcode">Индекс: </label>
          </div>
          <div class="rightTab">
            <input type="number" name="zipcode" id="zipcode" class="input-field" placeholder="Индекс">
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="country-label" for="country">Страна: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="country" id="country" class="input-field" placeholder="Страна">
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="region-label" for="region">Область: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="region" id="region" class="input-field" placeholder="Область">
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="city-label" for="city">* Город: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="city" id="city" class="input-field" placeholder="Город" v-model.trim="$v.city.$model">
            <span v-if="!$v.city.required && $v.city.$dirty">Введите город</span>
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="street-label" for="street">Улица: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="street" id="street" class="input-field" placeholder="Улица">
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="house-label" for="house">Дом: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="house" id="house" class="input-field" placeholder="Дом">
          </div>
        </div>
      </fieldset>

      <fieldset>
        <p>Паспорт</p>
        <div class="rowTab">
          <div class="labels">
            <label for="docType">* Тип документа</label>
          </div>
          <div class="rightTab">
            <select id="docType" name="docType" class="dropdown" v-model.trim="$v.docType.$model">
              <option disabled selected value>Выберите документ</option>
              <option value="Паспорт">Паспорт</option>
              <option value="Свидетельство">Свидетельство о рождении</option>
              <option value="Водительское">Вод. удостоверение</option>
            </select>
            <span v-if="!$v.docType.required && $v.docType.$dirty">Выберите тип документа</span>
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="series-label" for="series">Серия: </label>
          </div>
          <div class="rightTab">
            <input type="number" name="series" id="series" class="input-field" placeholder="Серия">
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="numberDoc-label" for="numberDoc">Номер: </label>
          </div>
          <div class="rightTab">
            <input type="number" name="numberDoc" id="numberDoc" class="input-field" placeholder="Номер">
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="gotByWhom-label" for="gotByWhom">Кем выдан: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="gotByWhom" id="gotByWhom" class="input-field" placeholder="Кем выдан">
          </div>
        </div>
        <div class="rowTab">
          <div class="labels">
            <label id="gotByDate-label" for="gotByDate">* Дата выдачи: </label>
          </div>
          <div class="rightTab">
            <input type="text" name="gotByDate" id="gotByDate" class="input-field" placeholder="Дата выдачи" v-model.trim="$v.gotByDate.$model">
            <span v-if="!$v.gotByDate.required && $v.gotByDate.$dirty">Введите дату выдачи</span>
          </div>
        </div>
      </fieldset>
      <button id="submit" type="submit">Создать клиента</button>
      <p class="typo__p" v-if="submitStatus === 'OK'">Новый клиент успешно создан!</p>
      <p class="typo__p" v-else-if="submitStatus === 'ERROR'">Корректно заполните необходимые данные</p>
    </form>
  </div>
</template>

<script>
  import { required } from 'vuelidate/lib/validators'
  export default {
    data: function () {
      return {
        surname: '',
        name: '',
        birthdate: '',
        phone: 7,
        clientGroup: [],
        city: '',
        docType: '',
        gotByDate: '',
        submitStatus: null
      }
    },
    validations: {
      surname: { required },
      name: { required },
      birthdate: { required },
      clientGroup: { required },
      phone: {},
      city: { required },
      docType: { required },
      gotByDate: { required }
    },
    methods: {
      submit() {
        console.log('submit!')
        this.$v.$touch()
        if (this.$v.$invalid) {
          this.submitStatus = 'ERROR'
        } else {
          this.submitStatus = 'OK'
        }
      }
    }
  }

</script>

<style lang="sass">
  header
    font-size: 2em
    font-weight: bold
    margin: 20px


  #form-outer
    background-color: rgb(250, 250, 250)
    margin: 0 auto
    border-radius: 4px
    width: 75%
    max-width: 900px
    padding: 10px
    padding-top: 20px

    .rowTab
      margin-top: 10px


  .labels
    display: inline-block
    text-align: right
    width: 40%
    padding: 5px
    vertical-align: middle
    margin-top: 10px


  .rightTab
    display: inline-block
    text-align: left
    width: 48%
    vertical-align: middle
    position: relative


  .input-field
    height: 20px
    width: 280px
    padding: 5px
    margin: 10px
    border: 1px solid #c0c0c0
    border-radius: 2px


  span
    position: absolute
    top: 30px
    left: 15px
    font-size: 12px
    color: red

  .userRatings,
  input[type="checkbox"]
    float: left
    margin-right: 5px


  #submit
    background-color: #59ace0
    border-radius: 4px
    color: white
    font-size: 1em
    height: 40px
    width: 96px
    margin: 10px
    border: 0 solid


  .multiselect
    height: 64px
    width: 140px
    padding: 5px
    margin: 10px
    margin-top: 15px
    border: 1px solid #c0c0c0
    border-radius: 2px


  .dropdown
    height: 35px
    width: 140px
    padding: 5px
    margin: 10px
    margin-top: 15px
    border: 1px solid #c0c0c0
    border-radius: 2px


  .radio, .checkbox
    position: relative
    left: -43px
    margin-left: 10px
    display: block
    padding-bottom: 10px


  @media screen and (max-width: 833px)
    .input-field
      width: 80%

    select
      width: 90%



  @media screen and (max-width: 520px)
    .labels
      width: 100%
      text-align: left

    .rightTab
      width: 80%
      float: left

    .input-field
      width: 100%

    select
      width: 100%


</style>
