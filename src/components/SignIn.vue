<!-- COMPONENTE BOILERPLATE -->

<template>
  <div class="container">
    <div class="header">
      <div class="header-description">
        <h3 class="header-title">Log In to You Did It! App</h3>
        <p class="header-subtitle">Start organizing your tasks!</p>
      </div>
    </div>

    <form @submit.prevent="signIn" class="form-sign-in">
      <div class="form">
        <div class="form-input">
          <label class="input-field-label">E-mail</label>
          <input
            type="email"
            class="input-field-login"
            placeholder="example@gmail.com"
            id="email"
            v-model="email"
            required
          />
        </div>
        <div class="form-input">
          <label class="input-field-label">Password</label>
          <input
            type="password"
            class="input-field-login"
            placeholder="**********"
            id="password"
            v-model="password"
            required
          />
        </div>

        <button class="button centered-button" type="submit">Sign In</button>
        <p>
          Dont have an account yet?
          <PersonalRouter
            :route="route"
            :buttonText="buttonText"
            class="sign-up-link"
          />
        </p>
      </div>
    </form>

    <div v-show="errorMsg">{{ errorMsg }}</div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import PersonalRouter from "./PersonalRouter.vue";
import { supabase } from "../supabase";
import { useRouter } from "vue-router";
import { useUserStore } from "../stores/user";
import { storeToRefs } from "pinia";

// Route Variables
const route = "/auth/signup";
const buttonText = "Sign Up";

// Input Fields
const email = ref("");
const password = ref("");

// Error Message
const errorMsg = ref("");

// Router to push user once SignedIn to Homepage
const redirect = useRouter();

// Arrow function to Signin user to supaBase
const signIn = async () => {
  // AQU?? FALTA UNA CONDICIONAL
  {
    try {
      // calls the user store and send the users info to backend to logIn
      await useUserStore().signIn(email.value, password.value);
      // redirects user to the homeView
      redirect.push({ path: "/" });
    } catch (error) {
      // displays error message
      errorMsg.value = error.message;
      // hides error message
      setTimeout(() => {
        errorMsg.value = null;
      }, 5000);
    }
    return;
  }
  errorMsg.value = "error";
};
</script>

<style></style>
