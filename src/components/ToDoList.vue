<template>
    <div class="wrapper">
        <div class="container">
            <div class="box">
                <input v-model="inputValue"  class="input" type="text">
                <button :disabled="!inputValue" @click="addToDoItems" class="btn">create</button>
            </div>
           <ul class="list" >
                <li v-for="(item, index) in toDoItems"  :key="index" class="list__item" >{{ item }}</li>
           </ul>
        </div> 
    </div>
</template>

<script setup lang="ts">
    import { ref } from 'vue';

    const inputValue = ref<string>('');
    const toDoItems = ref<string[]>([]);

    function addToDoItems(){
        if(!inputValue.value) return

        toDoItems.value.push(inputValue.value)
        inputValue.value = ''
    }
</script>

<style scoped lang="scss">
.wrapper{
    padding: 100px 0;
}
button:disabled{
    opacity: 0.7;
}
.container{
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 15px;
}
.box{
    display: grid;
    grid-template-columns: 3fr 1fr;
    column-gap: 30px;
    margin-bottom: 30px;
}
.input{
    width: 100%;
    padding: 10px;
    color: #222;
    border-radius: 0;
    font-size: 16px;
}
.btn{
    width: 100%;
    padding: 20px;
    background-color: #222;
    color: #fff;
    font-size: 16px;
    line-height: 1;
    text-align: center;
    border: none;
    text-transform: uppercase;
}
.list{
    display: grid;
    row-gap: 20px;
    padding: 0;
    list-style: none;
    &__item{
        color: #222;
        padding: 10px;
        font-size: 16px;
        line-height: 18px;
        background-color: #c3c3c3;
    }
}
</style>