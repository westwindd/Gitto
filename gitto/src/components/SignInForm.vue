<template>
  <div class="form">
    <img src="path/to/your/logo.png" alt="Logo" />
    <h1>Sign in</h1>
    <input type="text" placeholder="Username" />
    <input type="password" placeholder="Password" />
    <button>Sign In</button>
  </div>
</template>

<script>
export default {
  name: "SignInForm",
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;800&family=Poppins:wght@400;600;800&display=swap');

* {
  box-sizing: border-box;
}

.form {
  background: #212529; /* Gradient from black to dark blue */
  padding: 0 50px;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  border-radius: 10px;
  box-shadow: 0 14px 28px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.22);
  font-family: 'Poppins', sans-serif; /* Use Poppins as the default font */
}

input {
  background: transparent; /* No background */
  border: none; /* No border */
  border-bottom: 1px solid #fffcef; /* Bottom border as line */
  padding: 10px 0;
  margin: 10px 0;
  width: 50%;
  color: #fffcef; /* Light text */
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
  font-family: 'Poppins', sans-serif; /* Use Poppins for inputs */
}

input::placeholder {
  color: #b0b0b0; /* Placeholder text color */
}

input:focus {
  border-bottom: 1px solid #0051ff; /* Change bottom border color on focus */
  box-shadow: 0 1px rgba(30, 60, 114, 0.5); /* Blue shadow on focus */
  outline: none; /* Remove default outline */
}

button {
  border: none;
  padding: 15px 20px;
  margin: 10px 0;
  width: 50%;
  background: linear-gradient(to right, #161a1d, #121416); /* Reverse gradient on hover */
  color: white;
  cursor: pointer;
  transition: background 0.3s ease, transform 0.3s ease;
  border-radius: 15px; /* More rounded corners */
  font-family: 'Montserrat', sans-serif; /* Use Montserrat for buttons */
}

button:hover {
  transform: scale(1.05); /* Slightly enlarge on hover */
}

h1 {
  color: #ffffff; /* Light text */
  margin-bottom: 20px;
  font-family: 'Montserrat', sans-serif; /* Use Montserrat for headings */
}
</style>