<script>
import Price from './components/Price.vue';

export default {
  components: {
     Price 
    },
  data() {
    return {
      price: 100,
    };
  },
};
</script>

<template>

  <main>
    <div>
      <Price v-model="price" />
    </div>

  </main>
</template>
