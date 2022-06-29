<template>
  <v-app>
    <menuComp />
    <v-container>
    <nuxt />
    </v-container>
  </v-app>
</template>

<script>
import {Component, Vue} from "nuxt-property-decorator";
import menuComp from '~/components/helper/menuComp.vue'
@Component({
  components: { menuComp }
})
export default class layout extends Vue{

}
</script>
