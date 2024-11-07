<template>
    <div>
      <h2 style="text-align: center; color: white;">Minha Caixa</h2>
      <p style="text-align: center; color: white;">
        Aqui você pode escanear o QR code da lixeira para acessar informações adicionais e gerenciar seus descartes.
      </p>
      <v-btn color="primary" dark @click="openScanner">Abrir Caixa</v-btn>
  
      <qrcode-stream v-if="showScanner" @decode="onDecode" @init="onInit"></qrcode-stream>
  
      <div v-if="qrResult" style="margin-top: 20px; color: white;">
        <h3>Resultado do QR Code:</h3>
        <p>{{ qrResult }}</p>
      </div>
    </div>
  </template>
  
  <script>
  import { QrcodeStream } from 'vue-qrcode-reader'
  
  export default {
    components: {
      QrcodeStream
    },
    data() {
      return {
        showScanner: false,
        qrResult: null
      }
    },
    methods: {
      openScanner() {
        this.showScanner = true;
      },
      onDecode(result) {
        this.qrResult = result;
        this.showScanner = false; // Fecha o scanner após decodificar
      },
      onInit(promise) {
        promise.catch(error => {
          console.error(error.message)
        })
      }
    }
  }
  </script>
  
  <style scoped>
  h2 {
    margin-bottom: 10px;
  }
  </style>
  