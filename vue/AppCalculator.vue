<template>
<div class="container mt-5 pt-5 ">
    <div class="row">
        <div class="col calculator text-center mx-auto">
      <input type="text" class="calculator-input" v-model="displayValue" disabled>
  
      <div class="calculator-keys">
        <button type="button" class="operator" @click="addToDisplay('+')">+</button>
        <button type="button" class="operator" @click="addToDisplay('-')">-</button>
        <button type="button" class="operator" @click="addToDisplay('*')">&times;</button>
        <button type="button" class="operator" @click="addToDisplay('/')">&divide;</button>
  
        <button type="button" @click="addToDisplay(7)">7</button>
        <button type="button" @click="addToDisplay(8)">8</button>
        <button type="button" @click="addToDisplay(9)">9</button>
  
        <button type="button" @click="addToDisplay(4)">4</button>
        <button type="button" @click="addToDisplay(5)">5</button>
        <button type="button" @click="addToDisplay(6)">6</button>
  
        <button type="button" @click="addToDisplay(1)">1</button>
        <button type="button" @click="addToDisplay(2)">2</button>
        <button type="button" @click="addToDisplay(3)">3</button>
  
        <button type="button" @click="addToDisplay(0)">0</button>
        <button type="button" class="decimal" @click="inputDecimal('.')">.</button>
        <button type="button" class="clear" @click="clear()">AC</button>
  
        <button type="button" class="equal-sign operator" @click="calculateResult()">=</button>
      </div>
    </div>
    </div>
</div>
  </template>
<script>
export default {
  data() {
    return {
      displayValue: "0",
      firstValue: null,
      operator: null,
      waitingForSecondValue: false,
    };
  },
  methods: {

    addToDisplay(value) {
      if(this.displayValue === "0"){
        this.displayValue = ""
        this.displayValue += value;

      }else if(!this.displayValue === ""){
        this.displayValue = ""
        this.displayValue += value;
      }else{
        this.displayValue += value;
      }
    },

    calculateResult() {
      try {
        this.displayValue = eval(this.displayValue).toString();
        
      } catch (error) {
        this.displayValue = "Error";
      }

    },

    inputDecimal() {
      if (!this.displayValue.includes('.')) {
        this.displayValue += '.';
      }
    },

    clear() {
      this.displayValue = '0';
      this.firstValue = null;
      this.operator = null;
    },
  },
};
</script>
  <style scoped>

.calculator {
    border: 1px solid #ccc;
    padding: 1rem;
    border-radius: 5px;
    max-width: 400px;

}

.calculator-input {
    width: 100%;
    font-size: 4rem;
    height: 70px;
    border: none;
    background-color: #252525;
    color: #fff;
    text-align: right;
    padding-left: 20px;
    padding-right: 20px;
}

button {
    display: inline-block;
    height: 50px;
    background-color: #fff;
    border-radius: 3px;
    border: 1px solid #c4c4c4;
    background-color: transparent;
    font-size: 2.5rem;
    color: #333;
}

button:hover {
    background-color: #eaeaea;
}

.operator {
    color: #2f6654;
}

.clear {
    background-color: #f0595f;
    border-color: #b0353a;
    color: #fff;
}

.clear:hover {
    background-color: #f17377;
}

.equal-sign {
    background-color: #448c74;
    border-color: #448c74;
    color: #fff;
    height: 100%;
    grid-area: 2/4/6/5;
}

.equal-sign:hover {
    background-color: #2f6654;
}

.calculator-keys {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 20px;
    padding: 20px
}


  </style>
  