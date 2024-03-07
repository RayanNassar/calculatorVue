<template>

    <div :class="keyBoardButtons" >
    
        <div class="operationEffect" v-for="(operations, index) in keyboardButtonsOperations" :key="operations" :class="buttonsOperationsClass + index + 'o'" >{{ operations }}</div>
        
        <div class="numbersEffect"  v-for="(item, index) in keyButtonsNumbers" :key="item" :class="buttonsNumbersClass + index + 'N'" >{{ item }}</div>
    
    </div>

</template>

<script setup >
import {ref, onMounted} from "vue";
import { defineEmits } from "vue"

let buttonsNumbersClass = ref ('buttonsNumbersClass')
let buttonsOperationsClass = ref ('buttonsOperationsClass')
let keyBoardButtons = ref ('keyBoardButtons')


let keyButtonsNumbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, '.']

let keyboardButtonsOperations = [ 'AC', '>', '%', '/', '*', '-', '+', '=']

let emit = defineEmits(['keys-event']);

onMounted(()=>{

    
    document.querySelectorAll('.numbersEffect, .operationEffect').forEach (H => {
        H.addEventListener('mouseover', () => {
            H.style.transform = 'scale(1.07)'
        })
        H.addEventListener('mouseleave', ()=>{
            H.style.transform = 'scale(1)'
        })
        H.addEventListener('click', () => {
            H.style.transform = 'scale(0.9)';
            // eventBus.emit('buttonsClicked', H)
            emit('keys-event',H.innerHTML)
        })
        // console.log(H)
        // H.addEventListener('keydown', (event) => {
        //     console.log('clicked')
        //     H.style.transform = 'scale(0.9)';
        //     emit('keys-event', event.key)
        // })
    })
    document.body.addEventListener('keydown', event => {
        emit('keys-event', event.key)
    })
})
// const keydownEvent = (event) => {

//     console.log(event)

// }



</script>

<style scoped >

html ,body {
    font-size: 10px;
}

.keyBoardButtons {
    display:grid;
    align-items: center;
    justify-items: center;
    width:100%;
    height:100%;
    grid-area : 6/1/12/5;
    /* grid-template-columns: repeat(4, auto);
    grid-template-rows: repeat(5, auto); */
    grid-template-areas : 
    'AC backSpace percentage dived'
    'VII VIII IN times'
    'IV V VI mince'
    'I II III plus'
    'nothing nothing point equal'

}



[class *= buttonsNumbersClass], [class *= buttonsOperationsClass] {
    width:5.9rem;
    height: 5.9rem;
    border-radius: 50%;
    color:white;
    font-size: 3.2rem;
    display:flex;
    justify-content: center;
    align-items: center;
    transition: 0.5s;
}

[class *= buttonsOperationsClass] {
    background-color:#6AD439 ;
}
[class *= buttonsNumbersClass] {
    background-color: rgb(255, 255, 255, 0.2);
}

.buttonsOperationsClass0o {
    grid-area: AC;
}

.buttonsOperationsClass1o {
    grid-area: backSpace;
}

.buttonsOperationsClass2o {
    grid-area: percentage;
}

.buttonsOperationsClass3o {
    grid-area: dived;
}

.buttonsOperationsClass4o {
    grid-area: times;
}   

.buttonsOperationsClass5o {
    grid-area: mince;
}

.buttonsOperationsClass6o {
    grid-area: plus;
}

.buttonsOperationsClass7o {
    grid-area: equal;
}

.buttonsNumbersClass0N {
    grid-area: nothing;
    width:110px;
    height: 50px;
    border-radius: 20px;
}

.buttonsNumbersClass1N {
    grid-area: I;
}

.buttonsNumbersClass2N {
    grid-area: II;
}

.buttonsNumbersClass3N {
    grid-area: III;
}

.buttonsNumbersClass4N {
    grid-area: IV;
}

.buttonsNumbersClass5N {
    grid-area: V;
}

.buttonsNumbersClass6N {
    grid-area: VI;
}

.buttonsNumbersClass7N {
    grid-area: VII;
}

.buttonsNumbersClass8N {
    grid-area: VIII;
}

.buttonsNumbersClass9N {
    grid-area: IN;
}

.buttonsNumbersClass10N {
    grid-area: point;
}

@media (min-width:992px) and (max-width:1023px) {
    html {
        font-size: 10px;
    }
}
@media (min-width:1024px) {
    html, body {
        font-size: 12px;
    }
}

@media (max-width:768px) {
    html, body {
        font-size: 5px;
    }
}



/* //[ 'AC', '>', '%', '/', '*', '-', '+', '='] */
</style>