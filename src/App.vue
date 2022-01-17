<template>
  <form @submit.prevent="someAction()" class="registr">
    <h1>Регистрация</h1>
    
    <div>
      <input type="text"  placeholder="Введите номер серию паспорта" v-model="passport" title="Введите номер серию паспорта" >
      
    </div>

    
    <div> <input type="date"   v-model="year" @blur="$v.Date.$touch()"  title="Введите дату своего рождения"   > </div>

    <div><input type="email" id="email"   v-model.trim="email" placeholder="Электронный адрес" title="Введите свой email" ></div>
    <div><input type="number" v-model="age"  placeholder="Введите ваш возраст" name="age" title="Возраст" ></div> 
    <div><input type="tel" id="tel" v-model="tel"   placeholder="+7(___)___-__-__"  title="Введите свой номер телефона" > </div>
   
   
    <div>
      <input type="text" placeholder="Имя"  v-model="name" @blur="$v.name.$touch()" title="Введите свое имя"> 
    </div>

    <button type="submit" id="btn" :hidden="$v.$invalid">
      Регистрация
    </button>
  </form>
</template>

<script>
import { required, maxLength, email, numeric } from 'vuelidate/lib/validators';


export default {
  data() {
    return {
      passport:'' ,
      name: '',
      year:'' ,
      tel: '',
      age:'',
      email:'',

    };
  },

 
  validations: {
    
    passport: {
      required,numeric
      
    },
    year: {
      required,numeric
    },
    name: {
      required,
      maxLength: maxLength(10),
     
    },
    tel:{required,numeric
       
     
    },
    age:{required,numeric
       
    },
    email:{ required,
    email

    }
  },
};
</script>












<style>
* {
    
    padding: 0;
    box-sizing: border-box;}


.registr {
    background: #F1F5FE;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    
}
.registr input{
    padding: 5px;
    margin: 5px;
    width: 250px;
    height: 50px;
    border-radius: 10px;
}
.registr input:hover{
    background-color: aquamarine;}


#btn{
    border-radius: 10px;
    height: 40px;
    width: 100px;

}
#btn:hover{
    background-color: rgb(51,255,153);  
}


input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>

