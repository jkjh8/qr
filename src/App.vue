<template>
  <v-app>
    <v-app-bar flat app color="white">
      <v-spacer/>
      <div class="text-overline font-weight-light" >
        {{ value }}
      </div>
    </v-app-bar>
    <v-main app >
      <qrcode-vue :value="value" :size="size" level="H" class="img_center"></qrcode-vue>
    </v-main>
    <v-footer app color="white" class="text-overline font-weight-light">
      <v-row align="center" justify="center">
        <v-img        
        src='./assets/logo1.png'
        max-width="15"
        class="mr-2"
      ></v-img>
        Media Consulting
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
import axios from 'axios'
import QrcodeVue from 'qrcode.vue'
export default {
  name: 'App',
  components: {
    QrcodeVue
  },
  mounted () {
    this.getIp()
  },
  data: () => ({
    value: '',
    size: 200
  }),
  methods: {
    getIp () {
      axios.get("http://localhost:12300").then(res =>
        this.value = res.data
      )
    }
  }
}
</script>

<style>
.img_center {
  position: fixed;
  top: 40%;
  left: 47%;
  margin-top: -50px;
  margin-left: -45px;
  width: 200px;
  height: 200px;
}
</style>
