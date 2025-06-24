<script setup>
import { ref } from "vue";

// константы 
const name = ref(''); 
const tel = ref('');
// const date = ref('');
// const time = ref('');

// константы для ошибок
const Errorname = ref('');
const Errortelef = ref('');
// const Errordate = ref('');
// const Errortime = ref('');

// константы чтобы потом показать что натворили
const sucMassage = ref('');
const ShowInfo = ref(false);

const regInfo = ref ({ 
  name: "",
  tel: ""
});

function formaReg() { 
  // функция для формы регистрации на боулинг
  Errorname.value = "";
  Errortelef.value = "";
  // Errordate.value = "";
  // Errortime.value = "";

  let hasError = false;

  if (!name.value.trim()) {
    Errorname.value = "Введите имя";
    hasError = true; // исправлено
  } else if (!/^[А-Яа-я\s]+$/.test(name.value)) {
    Errorname.value = "Имя на кириллице";
    hasError = true; // исправлено
  }
  
  if (tel.value.length < 11) {
    Errortelef.value = "Телефон минимум 11 символов";
    hasError = true; // исправлено
  }

  if (!hasError) {
    sucMassage.value = `Заказ оформлен. ${name.value}`; // исправлено

    regInfo.value = {
      name: name.value,
      tel: tel.value
    };
    ShowInfo.value = true;
  }
}
</script>

<template>
<h1>ФОРМА БРОНИРОВАНИЯ</h1>

<div class="form"> 
  <label> Имя <input type="text" v-model="name"></label><br>
  <span style="color:red;">{{ Errorname }}</span><br> 
  <label> Телефон <input type="tel" v-model="tel"></label><br>
  <span style="color:red;">{{ Errortelef }}</span><br> 
  <label> Дата <input type="date"></label><br>
  <label> Время <input type="time"></label><br>
  <button @click="formaReg">Отправить</button> 
  <!-- вызов функции по кнопке -->
</div>

<br>

<div class="footer">
  Контакт: +79119829122
  Все права защищены 
</div>

<div v-if="ShowInfo">{{ sucMassage }}</div> 
</template>


<style scoped>
.footer{
  width: 100%;
  border: black 1px solid;
  text-align: center;
  justify-content: center;
}
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
