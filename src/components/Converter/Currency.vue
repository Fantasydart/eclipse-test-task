<template>
    <div class="content">
        <div class="main-currency"></div>
        <img src="@/assets/double-arrow.svg" alt="">
        <div class="support-currency"></div>
    </div>
</template>

<script>
    import { ref, toRef } from 'vue'
    export default {
        props: {
            currencyList: {
                type: Object,
                required: true
            }
        },
        setup(props){
            const currencyListLocal = toRef(props, 'currencyList')
            const firstCurrency = ref(null)
            const secondCurrency = ref(null)
            console.log(currencyListLocal.value)
            return {firstCurrency, secondCurrency}
        }
    }
</script>

<style scoped>
.content{
    width: 100%;
    min-height: 500px;
    background-color: #a0ffa05f;
    border-radius: 12px;
}
    img{
        width: 40px;
        height: 30px;
    }
</style>