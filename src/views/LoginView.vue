<script setup>
  import { reactive } from 'vue';
  import { useUserStore } from '../stores/user';

  const userStore = useUserStore();

</script>
<template>
    <div class="container">
        <h2>Login</h2>
        <form>
            <label for="username">Username:</label>
            <input type="text" id="username" name="username" required v-model="userStore.user.username">

            <label for="password">Password:</label>
            <input type="password" id="password" name="password" required v-model="userStore.user.password">

            <button type="submit" @click="userStore.validationLogin">Login</button>
        </form>
    </div>
</template>


<style scoped>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
    }

    .container {
      max-width: 400px;
      padding: 20px;
      background-color: #fff;
      border-radius: 5px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      margin-top: 10%;
    }

    .container h2 {
      text-align: center;
      margin-bottom: 20px;
    }

    .container label {
      display: block;
      margin-bottom: 10px;
      font-weight: bold;
    }

    .container input[type="text"],
    .container input[type="password"] {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      margin-bottom: 20px;
    }

    .container button[type="submit"] {
      width: 100%;
      padding: 10px;
      font-weight: bold;
      background-color: #4CAF50;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    .container button[type="submit"]:hover {
      background-color: #45a049;
    }
</style>