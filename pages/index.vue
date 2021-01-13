<template>
    <div class="container">
        <div>
            <Logo />
            <h1 class="title">flatrateCalculator</h1>
            <input type="text" v-model="raw" @keyup="calculateFlat">
            <hr>
            da pagare: {{toPay}}
            <hr>
            netto:
            {{clean}}

        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            raw: "",
            clean: "",
            toPay:""
        }
    },
    mounted() {
        this.raw = '';
        this.clean = '';
        this.toPay = '';

        },
    methods: {
        calculateFlat: function(event) {
            let taxable = (this.raw * 78)/100
            let previdence = ( taxable * 25.7)/100
            let flat_rate = ((taxable - previdence) * 15) / 100
            this.toPay = previdence + flat_rate
            this.clean = this.raw - (flat_rate + previdence)
        },
    },
};
</script>

<style>
.container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.title {
    font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    color: #35495e;
    letter-spacing: 1px;
}

.subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
}

.links {
    padding-top: 15px;
}
</style>
