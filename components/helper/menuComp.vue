<template>
  <div class="d-block menu-container">
    <v-container>
      <nav class="nav">
        <nuxt-link to="/" class="nav-log">
          <img src="~/assets/images/mobileshop.png" alt="" class="nav-logo-img">
        </nuxt-link>
        <ul class="nav-ul">
          <li class="nav-ul-li" v-for="(item,i) in menuLinks" :key="i">
            <nuxt-link exact v-if="item.link" active-class="nav-ul-li-active-route" :to="item.route" class="nav-ul-li-link">
              {{item.text}}
            </nuxt-link>
            <span v-if="item.dropdown"  class="nav-ul-li-link">
              Mobiles
              <Icon class="nav-ul-li-icon" v-if="item.dropdown" icon="bxs:down-arrow" />
            </span>
          </li>
        </ul>
        <ul class="nav-login">
          <li class="nav-login-li">
            <nuxt-link exact to="/login" class="nav-login-li-link">
              Login
              <Icon icon="simple-line-icons:login" class="nav-login-li-icon"/>
            </nuxt-link>
          </li>
        </ul>
      </nav>
    </v-container>
  </div>
</template>

<script lang="ts">
import { Icon } from '@iconify/vue2';
import {Component, Vue} from "nuxt-property-decorator";
@Component({
  name : 'menuComp',
  components: {
    Icon,
  }
})
export default class menuComp extends Vue{
  menuLinks : Array<object> = [
    {
      id: 0,
      text: "Home",
      route: '/',
      link: true
    },
    {
      id: 1,
      text: "Mobiles",
      dropdown: true,
      link: false,
      route: '/'
    },
    {
      id: 2,
      text: "AboutUs",
      route: '/about',
      link: true
    },
    {
      id: 3,
      text: "ContactUs",
      route: '/contactus',
      link: true
    },
  ]
}
</script>

<style lang="scss" scoped>
.menu-container {
  background: rgba(0, 0, 0, 0.92);
  height: 64px;
  & .nav {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    position: sticky;
    top: 0;
    width: 100%;
    &-logo{
      &-img{
        height: 48px;
      }
    }
    &-ul {
      display: flex;
      justify-content: center;
      list-style: none;
      align-items: center;
      padding: 0;
      margin: 0;
      &-li{
        cursor: pointer;
        margin-right: 48px;
        &-link{
          text-decoration: none;
          color: #F1F1F1;
          font-family: openSansMeduim;
          font-size: 14px;
          position: relative;
          transition: all .3s;
          height: 100%;
        }
        &-link::after , &-active-route:after{
          content: '';
          width: 0;
          height: 3px;
          position: absolute;
          bottom: -15px;
          border-radius: 50px;
          left: 0;
          right: 0;
          background-color: red;
          transition: all .3s
        }
        &-active-route:after{
          width: 100% !important;
        }
        &-link:hover::after{
          width: 100%;
        }
        &-link:hover{
          color: orangered;
        }
        &-active-route{
          color: orangered;
        }
        &-icon{
          color: inherit;
          position: relative;
          top: 3px;
          left: 8px;
        }
      }
    }
    &-login{
      list-style: none;
      padding: 0;
      margin: 0;
      &-li{
        color: var(--primary-color);
        transition: all .3s;
        &-link{
          display: flex;
          align-items: center;
          margin-right: 8px;
          text-decoration: none;
          color: inherit;
        }
        &-icon{
          margin-left: 8px;
          color: inherit;
        }
      }
      &-li:hover{
        color: orangered;
      }
    }
  }
}
</style>
