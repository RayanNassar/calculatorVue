<script setup >
import { ref } from "vue";
import keyBoards from "./components/keyBoard.vue"
import calculationsOp from './components/calculationsOperationsPart.vue'

let containerDiv = ref ('containerDiv');
// let keyBoardClassName = ref ('keyBoardClassName')


</script>

<template>

  <div :class="containerDiv" >
    <!-- <keyBoards></keyBoards> -->
    <calculationsOp></calculationsOp>
  <div class="splitParts" ></div>  
  </div>

</template>



<style scoped > 

.containerDiv {
  width:25%;
  height:95%;
  border-radius: 27px;
  border:2px solid rgb(255, 255, 255, 0.4);
  display:grid;
  grid-template-columns: repeat(4, 1fr) ;
  grid-template-rows: repeat(11, 1fr);
  overflow:hidden;
  align-items: center;
  justify-items: center;
}

.splitParts {
  width:90%;
  height:3%;
  background-color: white;
  grid-column: 1/5 ;
  grid-row : 5;
  border-radius: 6px;
}

@media (max-width:900px) {
  .containerDiv {
    width:31%;
  }
}

@media (max-width:1052px) {
  .containerDiv {
    width:27%;
  }
}

@media (max-width:880px) {
  .containerDiv {
    width:32%;
  }
}

@media (max-width:750px) {
  .containerDiv {
    width:40%;
  }
}
@media (max-width:580px) {
  .containerDiv {
    width:50%;
  }
}
@media (max-width:500px) {
  .containerDiv {
    width:fit-content;
  }
}

</style>