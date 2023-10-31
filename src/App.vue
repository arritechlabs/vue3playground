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
    const data = ref(null);

    onMounted(async () => {
      try {
        const response = await fetch("https://qgenonlinestaging.com/");

        if (!response.ok) {
          throw new Error(`HTTP error! Status: ${response.status}`);
        }

        data.value = await response;

        console.log(data.value);
      } catch (error) {
        console.error("There was a problem with the fetch operation:", error);
      }
    });

    return {
      data,
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
