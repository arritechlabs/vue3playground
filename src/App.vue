<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import { ref, onMounted } from "vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },

  setup() {
    const loginResponse = ref(null);

    const login = async () => {
      try {
        loginResponse.value = await fetch(
          "https://qgenonlinestaging.com/cfm-api/v1/ping",
          {
            method: "GET",
            headers: {
              "Content-Type": "application/json",
            },
          }
        );
      } catch (error) {
        console.error("Error logging in:", error);
      }
    };

    onMounted(() => {
      login();
    });

    return {
      loginResponse,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
