<script setup>
import {ref } from "vue";

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
})

function formaReg() {
 Errorname.value = "";
 Errortelef.value = "";
 Errordate.value = "";
 Errortime.value = "";

 let hasError = false;
 if(!name.value.trin()){
  Errorname.value = "введите имя"
  let hasError = true;
 }else if ([!А-Яа-я\s]+$/.test(name.value)) {
  Errorname.value = "Имя на кириллице"
  let hasError = true;
 }
 if(telef.value.length < 11){
  Errortelef.value = "Телефон минимум 11 символов";
  let hasError = true;
 }

 if(!hasError){
  sucMassage.value = "Заказ оформлен. ${name.value}";

  regInfo.value = {
      name: name.value;
      tel: tel.value;

  }
  ShowInfo.value = true;
 }
  
}

</script>

<template>
<h1>ФОРМА БРОНИРОВАНИЯ</h1>

<div class="form"> 
  <!-- делаем форму -->
   <label> Имя <input type="text" v-model="name"></label><br>
   <label> Телефон <input type="tel" v-model="tel"></label><br>
   <label> Дата <input type="date"></label><br>
   <label> Время <input type="time"></label><br>
   <button @click="formaReg(name, tel)">Отправить</button>

</div>

<div class="footer">
  Контакт: +79119829122
  Все права защищены 
</div>

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
