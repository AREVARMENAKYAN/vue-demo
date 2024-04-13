<script>
import Name from './Name.vue';
import Price from './Price.vue';
import Description from './Description.vue';

export default {
    components: {
        Name,
        Price,
        Description
    },

    props: {
        fruit: {
            type: Object,
            required: true
        }
    },
    methods: {
        buttonClick() {
            this.$emit('currencyChange');
        }
    },

}


</script>


<template>
    <div>
        
        <Name :value="fruit.name" /> 
        <Price :value="fruit.price" />
        <Description :value="fruit.description" />
        <button @click="buttonClick">Change the currency</button>
    </div>



</template>