<script>
export default {
  props:  {
    price:{
        type:Number,
        required:true
    }
  },
  
  data() {
    return {
      isDollar: true,
    };
  },
  methods: {
    changeCurrency() {
      if (this.isDollar) {
        this.$emit('update:price', this.price * 400);
        this.isDollar = false;
      } else {
        this.$emit('update:price', this.price / 400);
        this.isDollar = true;
      }
    },
  },
};
</script>

<template>
    <div>
        <h1>{{ price }}</h1>
        <button @click="changeCurrency">Change Currency</button>
      </div>

</template>