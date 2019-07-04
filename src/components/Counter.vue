<template>
    <span>
        {{ counter }} <button class="btn btn-primary btn-sm" @click="increaseCounter">+</button>
        <button class="btn btn-primary btn-sm" @click="decreaseCounter">-</button>
    </span>

</template>

<script>
export default {
    data(){
        return {
            counter: 0,
        }
    },
    methods:{
        increaseCounter(){
            this.counter += 1;
        },
        decreaseCounter(){
            this.counter -= 1;
        }
    }
}
</script>

<style scoped>

span{
    width:100px;
    margin-right: 10px;
}
button{
    margin-left: 5px;
}
</style>

