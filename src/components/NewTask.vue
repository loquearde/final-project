<template>
  <h1>Add a new Task</h1>
  <h3 class="date">And remember that today is {{ hoy }}</h3>
  <div v-if="showErrorMessage">
    <p class="error-text">{{ errorMessage }}</p>
  </div>
  <div class="container-inputs">
    <div class="input-field">
      <input
        type="text"
        placeholder="Add a Task Title - Listen to Kendrick Lamar"
        v-model="name"
      />
    </div>
    <div class="input-field">
      <input
        type="text"
        placeholder="Add a Task Description - Look up Kendrick Lamar's FEAR album on spotify and listen to the whole album."
        v-model="description"
      />
    </div>
    <button @click="addTask" class="button centered-button add-button">
      Add
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useTaskStore } from "../stores/task";
import moment from "moment";

const taskStore = useTaskStore();

const emit = defineEmits(["getTasksChild"]);

// variables para los valors de los inputs
const name = ref("");
const description = ref("");
const hoy = moment().format("dddd Do MMMM YYYY");

// constant to save a variable that holds an initial false boolean value for the errorMessage container that is conditionally displayed depending if the input field is empty
const showErrorMessage = ref(false);

// const constant to save a variable that holds the value of the error message
const errorMessage = ref(null);

// Arrow function para crear tareas.
const addTask = async () => {
  if (name.value.length === 0 || description.value.length === 0) {
    // Primero comprobamos que ningún campo del input esté vacío y lanzamos el error con un timeout para informar al user.

    showErrorMessage.value = true;
    errorMessage.value = "The task title or description is empty";
    setTimeout(() => {
      showErrorMessage.value = false;
    }, 5000);
  } else {
    // Aquí mandamos los valores a la store para crear la nueva Task. Esta parte de la función tenéis que refactorizarla para que funcione con emit y el addTask del store se llame desde Home.vue.

    await taskStore.addTask(name.value, description.value);
    name.value = "";
    description.value = "";

    emit("getTasksChild");
  }
};
</script>

<style></style>
