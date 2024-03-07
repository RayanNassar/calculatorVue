<template>
    
    <div :class="smallOutputClassName" >{{ smallOutputValue }}</div>

    <input type="text" :value="inputData" :class="outputPart" >

    <keyBoard @keys-event="importItems"></keyBoard>

</template>

<script setup >
import {ref, onMounted} from "vue";
import keyBoard from "./keyBoard.vue";


let outputPart = ref ('outputPart');
let inputData = ref ('')
let smallOutputClassName = ref ('smallOutputClassName')
let smallOutputValue = ref ('')

let operationsArr = [];

const importItems = H => {

    if (H == '=' || H == 'Enter') {

        let evalOutput = eval(inputData.value);
        operationsArr.push(evalOutput)
        smallOutputValue.value = inputData.value;
        inputData.value = evalOutput

        while (operationsArr.length) {
            operationsArr.pop()
        }
        console.log(operationsArr + ' before')
        operationsArr.push(evalOutput)
        console.log(operationsArr+' after')
    }
    else if (H == 'AC' || H == 'Delete'){

        smallOutputValue.value = '';
        inputData.value = ''

        while (operationsArr.length) {
            operationsArr.pop()
        }
        
    }
    else if (H == '&gt;' || H == 'Backspace') {
        operationsArr.pop();
        inputData.value = operationsArr.join('')
    }
    else if((!isNaN(Number(H)) && operationsArr.length == 0) || operationsArr.length) {
        operationsArr.push(H)
        inputData.value += H
    }
}

// onMounted (()=> {
     
// })

</script>

<style scoped >

.outputPart {
    border:none;
    background-color: transparent;
    color:white;
    font-size:3.2rem ;
    grid-row: 4;
    grid-column: 1/5;
    width:90%;
}

.smallOutputClassName {
    grid-row : 3;
    grid-column:3/5;
    width:100%;
    display:flex;
    height:100%;
    font-size: 1.9rem;
    justify-content: end;
    margin-right: 20px;
    align-items: flex-start;
    color:white;
}
</style>