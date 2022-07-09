<template>
  <div class="container">
    <h1>habbit tracker</h1>
    <p>
      Welcome to the habbit tracker app! Add a customisable table and start
      tracking your activities in a simple way!
    </p>
    <button>Add</button>
    <HabbitTracker />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import HabbitTracker from "@/components/HabbitTracker.vue";

export default defineComponent({
  name: "App",
  components: {
    HabbitTracker,
  },
});
</script>

<style lang="scss" scoped>
.container {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--pink);
  background-color: var(--white);
  height: 100vh;

  h1 {
    padding-top: 60px;
    text-transform: uppercase;
    font-weight: 600;
    margin-bottom: 20px;
    font-size: 2.5rem;
  }

  p {
    font-size: 1rem;
  }

  button {
    margin-top: 40px;
    width: 140px;
    height: 40px;
    color: var(--white);
    background-color: var(--pink);
    border: 2px solid var(--darker-pink);
    font-weight: 600;
    text-transform: uppercase;
    font-size: 0.9rem;
    cursor: pointer;

    &:hover {
      color: var(--darker-white);
    }
  }
}
</style>
