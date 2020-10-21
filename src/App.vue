<template>
  <v-app>
    <v-app-bar flat app color="white">
      <v-spacer/>
      <div class="text-overline font-weight-light" >
        {{ ipaddress }}
      </div>
    </v-app-bar>
    <v-main app >
      <qrcode-vue :value="value" :size="size" level="H"></qrcode-vue>
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
import myip from 'quick-local-ip'
import QrcodeVue from 'qrcode.vue'
export default {
  name: 'App',

  components: {
    QrcodeVue
  },

  data: () => ({
    value: 'http://' + myip.getLocalIP4(),
    size: 200,
    // ipaddress: 'http://' + window.location.hostname
    ipaddress: 'http://' + myip.getLocalIP4()
  })
}
</script>

<style>
#app {
  position: fixed;
  top: 40%;
  left: 47%;
  margin-top: -50px;
  margin-left: -45px;
  width: 200px;
  height: 200px;
}

</style>
