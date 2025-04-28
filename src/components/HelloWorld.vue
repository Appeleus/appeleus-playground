<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <div class="row">
      <button :disabled="counter >= 100" @click="addPointer()">+</button>
      <h3 class="center">{{ counter }}</h3>
      <button :disabled="counter >= 100" @click="deletePointer()">-</button>
    </div>
    <div v-for="point in pointer"> {{ point }}</div>

    <h3>
      <p> {{ counter < 100 ? "Get that count to 100 and see what happens lol" : "Here's ur reward" }} </p>
      <a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ" target="_blank" v-if="counter >= 100">https://www.youtube.com/watch?v=dQw4w9WgXcQ</a>
      <a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ" target="_blank" rel="noopener">Vite</a> +
      <a href="https://plaza.one/" target="_blank" rel="noopener">Vue 3</a>. What's next?
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}

button {
  width: 25%;
  height: 20px;
}

.center {
  text-align: center;
}
</style>

<script setup>
import { ref, defineProps, watch } from 'vue';

const props = defineProps({
  msg: String
});

const pointer = ref([]);

const counter = ref(0);

const addPointer = () => {
  counter.value++, 
  pointer.value.push('*');
};

const deletePointer = () => {
  counter.value--;
  pointer.value.pop();
};

watch(() => counter.value, (newVal, oldVal) => {
}, { deep: true });
</script>
