<template>
  <div class="auth-page" :class="{ 'right-panel-active': !isSignInPanelActive }">
    <div class="form-container sign-up-container">
      <SignUpForm />
    </div>
    <div class="form-container sign-in-container">
      <SignInForm />
    </div>
    <div class="overlay-container">
      <div class="overlay">
        <div class="overlay-panel overlay-left">
          <h1>Welcome Back!</h1>
          <p>If you already have an account please sign in here!</p>
          <button class="ghost" @click="switchToSignIn">Sign In</button>
        </div>
        <div class="overlay-panel overlay-right">
          <h1>Hello, Friend!</h1>
          <p>Enter your personal details and start your journey with us</p>
          <button class="ghost" @click="switchToSignUp">Sign Up</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SignInForm from "../components/SignInForm.vue";
import SignUpForm from "../components/SignUpForm.vue";

export default {
  components: {
    SignInForm,
    SignUpForm,
  },
  data() {
    return {
      isSignInPanelActive: true,
    };
  },
  methods: {
    switchToSignIn() {
      this.isSignInPanelActive = true;
    },
    switchToSignUp() {
      this.isSignInPanelActive = false;
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;800&family=Poppins:wght@400;600;800&display=swap');

* {
  box-sizing: border-box;
}

html, body {
  height: 100%;
  margin: 0;
  font-family: 'Poppins', sans-serif;
  background: #212529; /* Gradient from black to dark blue */
  color: #ffffff;
}

.auth-page {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(to bottom, #000011, #212529); /* Gradient from black to dark blue */
}

.form-container {
  background-color: #212529;
  border-radius: 10px;
  box-shadow: 0 14px 28px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.22);
  position: absolute;
  top: 0;
  height: 100%;
  width: 50%;
  transition: all 0.6s ease-in-out;
}

.sign-in-container {
  left: 0;
  z-index: 2;
}

.sign-up-container {
  left: 0;
  opacity: 0;
  z-index: 1;
}

.right-panel-active .sign-in-container {
  transform: translateX(100%);
}

.right-panel-active .sign-up-container {
  transform: translateX(100%);
  opacity: 1;
  z-index: 5;
}

.overlay-container {
  position: absolute;
  top: 0;
  left: 50%;
  width: 50%;
  height: 100%;
  overflow: hidden;
  transition: transform 0.3s ease-in-out;
  z-index: 100;
}

.right-panel-active .overlay-container {
  transform: translateX(-100%);
}

.overlay {
  background: linear-gradient(to left, #0a0a0b, #121517); /* Gradient from black to dark blue */
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 0 0;
  color: #ffffff;
  position: relative;
  left: -100%;
  height: 100%;
  width: 200%;
  transform: translateX(0);
  transition: transform 0.6s ease-in-out;
}

.right-panel-active .overlay {
  transform: translateX(50%);
}

.overlay-panel {
  position: absolute;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  text-align: center;
  top: 0;
  height: 100%;
  width: 50%;
  transform: translateX(0);
  transition: transform 0.6s ease-in-out;
}

.overlay-left {
  transform: translateX(-20%);
}

.right-panel-active .overlay-left {
  transform: translateX(0);
}

.overlay-right {
  right: 0;
  transform: translateX(0);
}

.right-panel-active .overlay-right {
  transform: translateX(20%);
}

.ghost {
  background: linear-gradient(to right, #161a1d, #212529); /* Gradient background */
  border: none;
  color: #ffffff;
  margin: 1rem;
  padding: 0.75rem 2rem;
  cursor: pointer;
  transition: all 0.3s ease;
  border-radius: 15px; /* Rounded corners */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Subtle shadow */
  font-family: 'Montserrat', sans-serif; /* Use Montserrat for buttons */
}

.ghost:hover {
  background: linear-gradient(to right, #161a1d, #212529); /* Reverse gradient on hover */
  transform: scale(1.05); /* Slightly enlarge on hover */
  box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15); /* Slightly larger shadow on hover */
}

/* Font sizes */
h1 {
  font-size: 24px;
  font-family: 'Montserrat', sans-serif; /* Use Montserrat for headings */
}

p {
  font-size: 14px;
  font-family: 'Poppins', sans-serif; /* Use Poppins for paragraphs */
}
</style>