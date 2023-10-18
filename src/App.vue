<template>
  <div class="container">
    <h1>Cifrado y Descifrado con Triple DES</h1>
    <p for="message">Mensaje:</p>
    <input type="text" v-model="message" id="message">
    <button @click="encrypt">Cifrar</button>
    <button @click="decrypt">Descifrar</button>
    <p class="results">{{ Text }}</p>
  </div>T
</template>

<script>
import CryptoJS from "crypto-js";

export default {
  data() {
    return {
      message: "",
      secretKey: "angel@encrypt",
      Text: "",
    };
  },
  methods: {
    encrypt() {
      const message = this.message;
      const secretKey = this.secretKey;

      const ciphertext = CryptoJS.TripleDES.encrypt(message, secretKey);
      this.Text = ciphertext.toString();
    },
    decrypt() {
      const message = this.message;
      const secretKey = this.secretKey;

      const bytes = CryptoJS.TripleDES.decrypt(message, secretKey);
      this.Text = bytes.toString(CryptoJS.enc.Utf8);
    },
  },
};
</script>

<style>
  body {
    margin-top: -10%;
    margin-left: 400px;
    background-color: #f7f7f7;
  }

  h1 {
    background-color: #3498db;
    color: white;
    padding: 10px;
    border-radius: 5px;
    text-align: center;
  }

  .container {
    margin: 20px;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  }

  input[type="text"] {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-bottom: 10px;
    font-size: 16px;
  }

  button {
    background-color: #3498db;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    margin-right: 20px;
  }

  button:hover {
    background-color: #258cd1;
  }

  .results {
    margin-top: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f7f7f7;
  }

  p {
    color: black;
  }
</style>