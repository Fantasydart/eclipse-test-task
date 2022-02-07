<template>
    <div class="content">
        <select name="currency" id="currency">
            <option value=""></option>
        </select>
    </div>
</template>

<script>
    export default {
        props: {
            currencyList: {
                type: Object,
                required: true
            }
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
</style>