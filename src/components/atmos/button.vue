<template>
    <button><slot>ボタン</slot></button>
</template>

<script>
export default {
    name: 'MyButton',
    methods: {
        clickHandler: function(){
            this.$emit('click')
        }
    }
}
</script>

<style>
button {
    border-radius: 85px;
    background: linear-gradient(145deg, #a4a4a4, #8a8a8a);
    box-shadow:  11px 11px 22px #828282,
             -11px -11px 22px #b0b0b0;
    margin: 20px;

}
</style>