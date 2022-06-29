<template>
  <div class="d-block menu-container">
    <v-container>
      <nav class="nav">
        <ul class="nav-ul">
          <li class="nav-ul-li" v-for="(item,i) in menuLinks" :key="i">
            <nuxt-link exact :to="item.route" active-class="nav-ul-li-active-route" class="nav-ul-li-link">
              {{item.text}}
            </nuxt-link>
            <Icon class="nav-ul-li-icon" v-if="item.dropdown" icon="bxs:down-arrow" />
          </li>
        </ul>
        <ul class="nav-login">
          <li class="nav-login-li">
            <nuxt-link to="/login" class="nav-login-li-link">
              Login
            </nuxt-link>
              <Icon icon="simple-line-icons:login" class="nav-login-li-icon"/>
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
    Icon
  }
})
export default class menuComp extends Vue{
  menuLinks : Array<object> = [
    {
      id: 0,
      text: "Home",
      route: '/'
    },
    {
      id: 1,
      text: "Mobiles",
      dropdown: true
    },
    {
      id: 2,
      text: "AboutUs",
      route: '/about'
    },
    {
      id: 3,
      text: "ContactUs",
      route: '/contactus'
    },
  ]
}
</script>

<style lang="scss" scoped>
.menu-container {
  background: rgba(0, 0, 0, 0.92);
  & .nav {
    display: flex;
    justify-content: space-between;
    position: sticky;
    top: 0;
    width: 100%;
    &-ul {
      display: flex;
      justify-content: space-around;
      list-style: none;
      align-items: center;
      padding: 0;
      margin: 0;
      width: 100%;
      &-li{
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
        &-icon{
          color: var(--primary-color);
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
        display: flex;
        align-items: center;
        &-link{
          margin-right: 8px;
          text-decoration: none;
          color: orangered;
          transition: all .3s;
        }
        &-link:hover{
          color: var(--primary-color);
        }
        &-icon{
          color: orangered;
        }
      }
    }
  }
}
</style>
