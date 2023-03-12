<template>
    <form @submit.prevent="submission">
      <label>Student Number:</label>
      <input type="stuNum" required v-model="StuNum">

      <label>Email:</label>
      <input type="email" required v-model="email">
  
      <label>Password:</label>
      <input type="password" required v-model="password">
      <div v-if="passwordError" class="error">{{ passwordError }}</div>
  
      <div class="terms">
          <input type="checkbox" v-model="terms" required>
          <label>Accept terms and conditions</label>
      </div>
  
      <div class="submit">
          <button>Login</button>
      </div>
  
    </form>
  </template>
  
  <script>
  export default {
      data() {
          return {
            StuNum: '',
            email: '',
            password: '',
            terms: false,
            passwordError: ''
          }
      },
      methods: {
          submission() {
              //validate password
              this.passwordError = this.password.length > 7 ? 
              '': 'Password must be at least 8 chars long'
          
          if(!this.passwordError) {
              console.log('email: ', this.email)
              console.log('password: ', this.password)
              console.log('terms accepted: ', this.terms)
          }
          }
      }
  }
  </script>
  
  <style scoped>
  form {
      max-width: 420px;
      margin: 41px auto;
      background: rgb(42, 42, 42);
      text-align: left;
      padding: 40px;
      border-radius: 10px;
  }
  label {
      color: #aaa;
      display: inline-block;
      margin: 25 px 0 15px;
      font-size: 0.6em;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: bold;
  }
  input{
      display: block;
      padding: 10px 6px;
      width: 100%;
      box-sizing: border-box;
      border: none;
      border-bottom: 1px solid #ddd;
      color: #555;
  }
  input[type="checkbox"] {
      display: inline-block;
      width: 16px;
      margin: 0 10px 0 0;
      position: relative;
      top: 2px;
  }
  .pill {
      display: inline-block;
      margin: 20px 10px 0 0;
      padding: 6px 12px;
      background: #eee;
      border-radius: 20px;
      font-size: 12px;
      letter-spacing: 1px;
      font-weight: bold;
      color: #777;
      cursor: pointer;
  }
  button {
      background: #ffdd00;
      border: 0;
      padding: 10px 20px;
      margin-top: 20px;
      color: white;
      border-radius: 20px;
  }
  .submit {
      text-align: center;
  }
  .error {
      color: #ff0000;
      margin-top: 10px;
      font-size: 0.8em;
      font-weight: bold;
  }
  </style>