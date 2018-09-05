<template>
    <div class="calculator">
        <div class="display">{{current || '0'}}</div>
        <div @click="clear" class="btn">AC</div>
        <div @click="negate" class="btn">+/-</div>
        <div @click="percentage" class="btn-warning">%</div>
        <div @click="divide" class="btn-warning">/</div>
        <div @click="append('7')" class="btn">7</div>
        <div @click="append('8')" class="btn">8</div>
        <div @click="append('9')" class="btn">9</div>
        <div @click="multiply" class="btn-warning">x</div>
        <div @click="append('4')" class="btn">4</div>
        <div @click="append('5')" class="btn">5</div>
        <div @click="append('6')" class="btn">6</div>
        <div @click="subtract" class="btn-warning">-</div>
        <div @click="append('1')" class="btn">1</div>
        <div @click="append('2')" class="btn">2</div>
        <div @click="append('3')" class="btn">3</div>
        <div @click="add" class="btn-warning">+</div>
        <div @click="append('0')" class="btn">0</div>
        <div @click="square" class="btn">sq.</div>
        <div @click="decimal" class="btn">.</div>
        <div @click="equal" class="btn-warning">=</div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      current: "",
      previous: null,
      operatorClicked: false,
      operator: null
    };
  },
  methods: {
    clear() {
      this.current = "";
    },
    negate() {
      this.current =
        this.current.charAt(0) === "-" | this.current.charAt(0) === ""
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    percentage() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = "";
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    decimal() {
      if (this.current.indexOf(".") === -1) {
        this.current = `${this.current}.`;
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    subtract() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    square(){
        this.operator = (a) => Math.pow(a, 2);
        this.setPrevious();
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.previous),
        parseFloat(this.current)
      )}`;
      this.previous = null;
    }
  }
};
</script>

<style>
.calculator {
  margin: 0 auto;
  width: 500px;
  font-size: 26px;
  box-shadow: 5px 10px 8px #888888;
  display: grid;
  border: 1px solid #333;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.display {
  grid-column: 1/5;
  display: block;
}
.btn {
  background-color: #eeeeee;
  border: 1px solid #333;
  font-size: 30px;
}
.btn:hover {
  background-color: #cccfff;
}
.btn-warning {
  border: 1px solid #333;
  font-size: 30px;
}
</style>


