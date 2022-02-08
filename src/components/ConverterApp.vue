<template>
    <div class="tabs">
        <div class="options">
            <div class="title" v-bind="isCurrency" @click="toggle(true, false)">Список валют</div>
            <div class="title" v-bind="isConverter" @click="toggle(false, true)">Конвертер</div>
        </div>
        <div class="content">
            <Currency v-if="isCurrency" :currencyList="list"/>
            <Converter v-if="isConverter" />
        </div>
    </div>
</template>

<script>
    import Currency from './Converter/Currency'
    import Converter from './Converter/Converter'
    import { ref, onMounted } from 'vue'
    import axios from 'axios'
    export default  {
        components: { Currency, Converter},
        setup(){
            const isCurrency = ref(true)
            const isConverter = ref(false)
            const list = ref([])
            onMounted(async () => {
                const res = await axios.get("https://www.cbr-xml-daily.ru/daily_json.js");
                list.value = res.data.Valute;
                console.log(res.data.Valute);
            });
            function toggle(currency, converter) {
                this.isCurrency = currency;
                this.isConverter = converter
            }

            return {list, isCurrency, isConverter, toggle }
        },
    }
</script>

<style scoped>
.options {
    display: flex;
    flex-direction: row;
}
    .options .title {
        padding: 12px 20px;
        border-radius: 4px;
        margin: 0 10px 20px 0;
        background-color: #f1f1f1;
    }
</style>