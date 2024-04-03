<script>

export default {

  data() {
    return {
      email: '',
      isEmailvalid: false,
    };
  },

  methods: {
    openEmailPrompt() {
      let email = prompt('Input your email');
      if (!email) {
        this.isEmailvalid = false;
        return;
      }
      email = email.trim();
      this.email = email;
      const isValid = this.checkIsEmailValid(email);
      this.isEmailvalid = isValid;
    },


    checkIsEmailValid(email) {
      const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
      return emailRegex.test(email);
    },


  }
}
</script>

<template>
  <main>
    <button @click="openEmailPrompt()">Input your email</button>
    <div v-if="email">
      <h1 class="green" v-if="isEmailvalid">{{ email }}</h1>
      <h1 class="red" v-else>{{ email }}</h1>
    </div>

    <h4>{{ `The email is ${isEmailvalid ? 'valid' : 'invalid'}` }}</h4>

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
