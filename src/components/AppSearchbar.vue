<script>
import { store } from "../store.js";
import AppCard from "./AppCard.vue";
export default {
  components: {
    AppCard,
  },
  data() {
    return {
      store,
    };
  },
};
</script>
<template>
  <div class="m-5">
    <h1 class="col-auto">Boolflix</h1>
    <div>
      <input
        type="text"
        placeholder="Cerca film"
        v-model="store.inputValue"
        @keydown.enter="$emit('search')"
      />
      <button @click="$emit('search')">Cerca</button>
    </div>
    <AppCard />
  </div>
</template>
<style scoped>
.m-5 {
  max-width: 100%;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  margin: 0 auto;
  align-items: center;
  justify-content: center;
}

.m-5 > * {
  margin-bottom: 15px;
}
</style>
