<script>
import { store } from "../store.js";
export default {
  data() {
    return {
      store,
    };
  },
};
</script>
<template>
  <div class="container-searchbar p-3">
    <h1 class="col-auto main-title">Boolflix</h1>
    <div class="d-flex align-content-center">
      <input
        class="searchbar"
        type="text"
        placeholder="Cerca film"
        v-model="store.inputValue"
        @keydown.enter="$emit('search')"
      />
      <button class="btn btn-sm" @click="$emit('search')">Cerca</button>
    </div>
  </div>
</template>
<style scoped>
.main-title {
  color: red;
  font-weight: bold;
}

.searchbar {
  background-color: rgba(240, 248, 255, 0.93);
}

.btn {
  background-color: gray;
}

.container-searchbar {
  background-color: rgba(0, 0, 0, 0.644);
  max-width: 100%;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  margin: 0 auto;
  align-items: center;
  justify-content: center;
}

.container-searchbar > * {
  margin-bottom: 15px;
}
</style>
