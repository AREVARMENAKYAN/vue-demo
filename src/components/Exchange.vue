<script>

export default {
    data() {
        return {
            value: 0,
            rate: 400,
            mode: 'AMD'
        };
    },

    methods: {
        handleInput(event) {
            this.value = event.target.value;
        },
        handleInputFocus() {
            if (+this.value === 0) {
                this.value = '';
            }
        },
        changeMode() {
            if (this.mode === 'AMD') {
                this.mode = 'USD';
            } else {
                this.mode = 'AMD';
            }
            this.value = 0;
        }
    }
};

</script>



<template>
    <div v-if="mode === 'AMD'">
        <h5>AMD -> USD</h5>
        <input type="number" :value="value" @input="handleInput" @focus="handleInputFocus" />
        <input type="number" disabled :value="value / rate" />
        <button @click="changeMode">USD->AMD</button>
    </div>

    <div v-else>
        <h5>USD -> AMD</h5>
        <input type="number" :value="value" @input="handleInput" @focus="handleInputFocus" />
        <input type="number" disabled :value="value * rate" />
        <button @click="changeMode">AMD -> USD</button>
    </div>


</template>