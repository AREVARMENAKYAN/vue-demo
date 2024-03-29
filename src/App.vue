<script>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

export default {

  data() {
    return {
      inputEmail: '',
      emailValid: false,
      checkedEmail: '',
      isEmailChecked: false,
    }
  },

  methods: {

    validateEmail(email) {
      const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
      return emailRegex.test(email);
    },

    checkEmail() {
      const email = prompt('Please enter your email');
      if (email) {
        this.checkedEmail = email;
        this.isEmailChecked = true;
        this.emailValid = this.validateEmail(email);
      }
    },

    resetEmail() {
      this.inputEmail = '';
      this.checkedEmail = '';
      this.emailValid = false;
      this.isEmailChecked = false;
    }

  }
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>

    <button @click="checkEmail">Input Email</button>
    <button @click="resetEmail">Reset</button>
    <div v-if="isEmailChecked">
      <h1 :style="{ borderColor: emailValid ? 'green' : 'red' }">{{ checkedEmail }}</h1>
      <h4 v-if="emailValid">The email is valid</h4>
      <h4 v-else>The email is invalid</h4>
    </div>



    <TheWelcome />
  </main>
</template>

<style scoped>
h1 {
  border: 2px solid;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
