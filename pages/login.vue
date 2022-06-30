<template>
  <div class="login">
    <form @submit.prevent="handleLogin"  class="login-form" method="post">
      <div class="login-form-div">
        <label for="email" class="login-label">Email :</label>
        <v-text-field name="email" type="email" class="login-input" outlined>
          <template #prepend-inner>
            <svg xmlns="http://www.w3.org/2000/svg" aria-hidden="true" role="img" width="24" height="24" preserveAspectRatio="xMidYMid meet" viewBox="0 0 24 24"><path fill="#AFAFAF" d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm-.4 4.25l-7.07 4.42c-.32.2-.74.2-1.06 0L4.4 8.25a.85.85 0 1 1 .9-1.44L12 11l6.7-4.19a.85.85 0 1 1 .9 1.44z"/></svg>
          </template>
        </v-text-field>
      </div>
      <div class="login-form-div">
      <label for="password" class="login-label">Password : </label>
        <v-text-field class="login-input" type="password" name="password" outlined>
          <template #prepend-inner>
<!--            <Icon icon="ri:lock-password-fill" />-->
            <svg xmlns="http://www.w3.org/2000/svg" aria-hidden="true" role="img" width="24" height="24" preserveAspectRatio="xMidYMid meet" viewBox="0 0 24 24"><path fill="#AFAFAF" d="M18 8h2a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H4a1 1 0 0 1-1-1V9a1 1 0 0 1 1-1h2V7a6 6 0 1 1 12 0v1zm-2 0V7a4 4 0 1 0-8 0v1h8zm-5 6v2h2v-2h-2zm-4 0v2h2v-2H7zm8 0v2h2v-2h-2z"/></svg>
          </template>
        </v-text-field>
      </div>
      <div class="login-form-div">
        <v-btn depressed type="submit" class="login-btn">
          LOGIN
        </v-btn>
      </div>
   <div class="login-form-div">
     <div class="login-go-register">
       <div class="login-forget-password">
         <nuxt-link class="login-forget-link" to="/forget">
           Forget password ?
         </nuxt-link>
       </div>
       <p class="login-go-register-text">You don't have an account ? Register from <nuxt-link to="/register" class="login-go-register-link">HERE</nuxt-link></p>
     </div>
   </div>
    </form>
  </div>
</template>

<script lang="ts">
import {Icon} from '@iconify/vue2'
import {Component, Vue} from "nuxt-property-decorator";
@Component({
  name: "login",
  layout: "login",
  components: {
    Icon,
  }
})
export default class Login extends Vue{
  handleLogin() {
    console.log('button clicked')
  }
}
</script>

<style lang="scss" scoped>
.login{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 100%;
  &-form{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 60%;
  }
  &-form-div{
    margin-top: 48px;
    width: 100%;
    display: grid;
    grid-template-columns: 1fr 5fr;
    align-items: center;
  }
  &-label{
    font-family: openSansMeduim;
    font-size: 16px;
  }
  &-input{
    border-radius: 12px;
    min-height: 36px;
    max-height: 48px;
    box-sizing: border-box;
  }
  &-btn{
    height: 48px !important;
    min-height: 48px !important;
    margin-top: 24px;
    width: 100%;
    color: white;
    background-color: orangered !important;
    border-radius: 12px;
    grid-column-start: 2;
    grid-column-end: 3;
  }
  &-go-register{
    //margin-top: 48px;
    grid-column-start: 2;
    grid-column-end: 3;
    &-text{
      font-family: openSansMeduim;
      font-size: 13px;
      color: gray;
    }
    &-link{
      text-decoration: none;
      font-family: openSansMeduim;
      font-size: 16px;
      transition: all .3s;
    }
    &-link:hover{
      color: orangered;
    }
  }
  &-forget-link{
    text-decoration: none;
    transition: all .3s;
  }
  &-forget-link:hover{
    color: orangered;
  }
}
</style>
<style>
.login-input .v-input__slot:focus-visible{
  outline: none !important;
}
.login-input:focus{
  outline: none !important;
  border: none !important;
}
.login-input fieldset{
  border: none !important;
  border-bottom: 1px solid #b4b7c3 !important;
  border-radius: 0 !important;
}
.login-input input{
  background: unset !important;
}
</style>
