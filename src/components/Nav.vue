<template>
  <nav class="navbar">
    <router-link to="/" class="navbar-logo"></router-link>
    <div class="toggle-menu">
      <label for="toggle-menu-checkbox">
        <img
          src="..//assets/images/hamburger-menu.png"
          alt="hamburger menu"
          class="burger-img"
        />
      </label>
    </div>
    <input
      type="checkbox"
      class="toggle-menu__checkbox"
      id="toggle-menu-checkbox"
    />
    <ul class="nav-menu">
      <li class="nav-item">
        <router-link to="/" class="nav-link">Task Manager</router-link>
      </li>
      <li class="nav-item">
        <router-link class="nav-link" to="/account">Account</router-link>
      </li>
    </ul>

    <div class="hide log-out">
      <ul>
        <li class="log-out-welcome">
          <p v-if="getUser">Welcome, {{ getUser.email }}</p>
        </li>
        <li>
          <button @click="signOut" class="button log-out-button">
            Log out
          </button>
        </li>
      </ul>
    </div>
    <div class="hamburger">
      <span class="bar"></span>
      <span class="bar"></span>
      <span class="bar"></span>
    </div>
  </nav>
</template>

<script setup>
// import PersonalRouter from "./PersonalRouter.vue";
import { useUserStore } from "../stores/user";
import { computed } from "vue";
import { useRouter } from "vue-router";
import { ref } from "vue";

//constant to save a variable that will hold the use router method
const route = "/";
const buttonText = "Todo app";

// constant to save a variable that will get the user from store with a computed function imported from vue
// const getUser = computed(() => useUserStore().user);
const getUser = useUserStore().user;

// constant that calls user email from the useUSerStore
const userEmail = getUser.email;

// async function that calls the signOut method from the useUserStore and pushes the user back to the Auth view.
const redirect = useRouter();

const signOut = async () => {
  try {
    // call the user store and send the users info to backend to signOut
    await useUserStore().signOut();
    // then redirect user to the homeView
    redirect.push({ path: "/auth/login" });
  } catch (error) {
    errorMsg.value = error.message;
    setTimeout(() => {
      errorMsg.value = null;
    }, 5000);
  }
  return;
};
</script>

<style>
/* .navbar-img {
  width: 90px;
}

nav {
  background-color: lightgray;
  display: flex;
  width: 100%;
  justify-content: space-around;
  align-items: center;
}

nav ul {
  list-style: none;
  padding-inline-start: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
} */
</style>
