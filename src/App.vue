<script>
export default {
  data() {
    return {
      display: '',
      operatorUsed: false,
    };
  },
  methods: {
    appendNumber(number) {
      this.display += number;
    },
    appendOperator(operator) {
      if (this.operatorUsed) return;
      this.display += operator;
      this.operatorUsed = true;
    },
    appendDecimal() {
      if (this.display.includes('.')) return;
      this.display += '.';
    },
    clearDisplay() {
      this.display = '';
      this.operatorUsed = false;
    },
    calculateResult() {
      try {
        this.display = eval(this.display).toString();
        this.operatorUsed = false;
      } catch (error) {
        this.display = 'Error';
      }
    },
  },
};
</script>

<template>
  <div id="app">
    <div class="calculator">
      <input
        type="text"
        v-model="display"
        disabled
        class="display"
      />
      <div class="buttons">
        <button @click="appendNumber('7')">7</button>
        <button @click="appendNumber('8')">8</button>
        <button @click="appendNumber('9')">9</button>
        <button @click="clearDisplay">C</button>
        <button @click="appendNumber('4')">4</button>
        <button @click="appendNumber('5')">5</button>
        <button @click="appendNumber('6')">6</button>
        <button @click="appendOperator('/')">/</button>
        <button @click="appendNumber('1')">1</button>
        <button @click="appendNumber('2')">2</button>
        <button @click="appendNumber('3')">3</button>
        <button @click="appendOperator('*')">*</button>
        <button @click="appendNumber('0')">0</button>
        <button @click="appendDecimal">.</button>
        <button @click="calculateResult">=</button>
        <button @click="appendOperator('-')">-</button>
        <button @click="appendOperator('+')">+</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  padding: 20px;
}

.calculator {
  display: inline-block;
  border: 1px solid #ddd;
  padding: 20px;
  border-radius: 10px;
  background-color: #f9f9f9;
}

.display {
  width: 200px;
  height: 40px;
  text-align: right;
  font-size: 24px;
  margin-bottom: 10px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 10px;
}

button {
  font-size: 20px;
  padding: 10px;
  cursor: pointer;
  border: 1px solid #ddd;
  border-radius: 5px;
  background-color: #f0f0f0;
}

button:hover {
  background-color: #ddd;
}
</style>
