<script>

export default {

  data() {
    return {
      email: '',
      isEmailValid: false,
    };
  },

  methods: {
    openEmailPrompt() {
      let email = prompt('Input your email');
      if (!email) {
        this.isEmailValid = false;
        return;
      }
      email = email.trim();
      this.email = email;
      const isValid = this.checkIsEmailValid(email);
      this.isEmailValid = isValid;
    },


    checkIsEmailValid(email) {
      const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
      return emailRegex.test(email);
    },


    reset() {
      this.email = '';
      this.isEmailValid = false;
    }
  }
}
</script>

<template>
  <main>
    <button @click="openEmailPrompt()">Input your email</button>
    <button @click="reset()">Reset</button>
    <!-- <div v-if="email">
      <h1 class="green" v-if="isEmailValid">{{ email }}</h1>
      <h1 class="red" v-else>{{ email }}</h1>
    </div> -->

    <h1 :class="isEmailValid ? 'green' : 'red'" v-if="email">{{ email }}</h1>

    <h4 v-if="email">{{ `The email is ${isEmailValid ? 'valid' : 'invalid'}` }}</h4>

  </main>
</template>

<style scoped>
.red {
  border: 1px solid red;
}

.green {
  border: 1px solid green;
}
</style>
