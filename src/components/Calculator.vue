<template>
  <div class="calculator">
    <div class="display">{{ current || '0' }}</div>
    <div @click="clear" class="btn">c</div>
    <div @click="del" class="btn">del</div>
    <div @click="percent" class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="times" class="btn operator">x</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="subtract" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="append('0')" class="btn">0</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="btn operator">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      previous: null,
      current: '',
      operator: null,
      operatorClicked: false,
      isActive: false
    };
  },
  methods: {
    clear() {
      this.current = '';
      this.previous = null;
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ?
        this.current.slice(1) : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;

      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      if(this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    del() {
      this.current = this.current.slice(0, -1);
    },
    divide() {
     this.operator = (a, b) => a / b;
     this.setPrevious();
    },
    times() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    subtract() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
      console.log(this.operator);
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
      console.log(this.operator);
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px auto);
  font-size: 40px;
  width: 400px;
  /* margin: 0 auto; */
}

.calculator > div:active {
  opacity: 0.5;
}

.display {
  grid-column: 1/5;
  background-color: #2B3848;
  color: white;
  text-align: right;
  padding-right: 15px;
  font-family: 'Montserrat', sans-serif;
}

/* .zero {
  grid-column: 1/3;
} */

.btn {
  background-color: #303B4B;
  border: 1px solid #222831;
  color: white;
}

.operator {
  background-color: #263342;
  color: #3ADBC4;
}

.zero, .btn, .operator {
  cursor: pointer;
  text-align: center;
  transition: opacity 0.4s;
  opacity: 1;
  font-family: 'Montserrat', sans-serif;
}

/* .zero:hover, .btn:hover, .operator:hover {
  opacity: 0.5;
  transition: opacity 0.4s;
} */

@media only screen and (max-width: 600px) {
  .calculator {
    width: 300px;
  }


}

@import url('https://fonts.googleapis.com/css?family=Montserrat:200');



</style>
