<template>
    <div class="container">
      <div class="row">
        <div class="col-lg-10 col-xl-9 mx-auto">
          <div class="card flex-row my-5 border-0 shadow rounded-3 overflow-hidden custom-shadow">
            <div class="card-img-left d-none d-md-flex">
            </div>
  
            <div class="card-body p-4 p-sm-5">
              <h5 class="card-title text-center mb-5 fs-2 font-weight-bold">Encriptación con libreria CryptoJS</h5>
  
              <div class="form-floating mb-3">
                <input v-model="inputText" type="text" class="form-control" required autofocus />
                <label for="input">Texto a cifrar</label>
              </div>
  
              <div class="d-flex mb-2">
                <button @click="cifrarTexto" class="btn btn-lg btn-primary btn-login fw-bold text-uppercase" type="submit">Encriptar</button>
                <button @click="descifrarTexto" class="btn btn-lg btn-success btn-login fw-bold text-uppercase" type="submit">Desencriptar</button>
              </div>
  
              <div class="form-floating mb-3">
                <input v-model="outputText" type="text" class="form-control" required />
                <label for="output">Salida</label>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>

<script>
import CryptoJS from 'crypto-js';

export default {
  data() {
    return {
      inputText: '',
      outputText: ''
    };
  },
  methods: {
    cifrarTexto() {
      const clave = 'claveDeCifrado'; // La clave para el cifrado
      const textoCifrado = CryptoJS.AES.encrypt(this.inputText, clave).toString();
      this.outputText = textoCifrado;
    },
    descifrarTexto() {
      const clave = 'claveDeCifrado'; // La clave para el cifrado (debe ser la misma que usaste para cifrar)
      const textoDescifrado = CryptoJS.AES.decrypt(this.inputText, clave).toString(CryptoJS.enc.Utf8);
      this.outputText = textoDescifrado;
    }
  }
};
</script>

<style scoped>
html, body {
  height: 100%; /* Asegura que el cuerpo ocupe toda la altura de la ventana */
  margin: 0;
  padding: 0;
}

body {
  background: url('@/assets/background.png') no-repeat center center fixed;
  background-size: cover;
}
.card-img-left {
    width: 45%;
    background: scroll center url('@/assets/cifrado-login.png');
    background-size: cover;
  }
  
  .btn-login {
    font-size: 0.9rem;
    letter-spacing: 0.05rem;
    padding: 0.75rem 1rem;
    border-radius: 10px;
    width: 200px;
  }
  
  .d-flex {
    justify-content: space-between;
    margin-top: 30px;
  }
  
  .form-floating {
    margin-top: 30px;
  }
  
  .btn-primary {
    margin-right: 10px;
  }
  
  .custom-shadow {
    box-shadow: 0 5 20px rgba(0, 0, 0, 0.566);
  }
  
  .text-primary {
    text-decoration: none;
  }
</style>
