<template>
  <div id="calculator">
    <h1 class="title">Kaklator</h1>
    <div class="calculator--wrapper">
      <div id="calculator--wrapper---output"> {{ displayValue }}</div>

      <div class="calculator-buttons">
        <button class="cee" @click="clear()">C</button>
        <button @click="operator = 'divide'">÷</button>

        <button @click="setNumber(7)">7</button>
        <button @click="setNumber(8)">8</button>
        <button @click="setNumber(9)">9</button>
        <button @click="operator = 'multiply'">×</button>

        <button @click="setNumber(4)">4</button>
        <button @click="setNumber(5)">5</button>
        <button @click="setNumber(6)">6</button>
        <button @click="operator = 'subtract'">−</button>

        <button @click="setNumber(1)">1</button>
        <button @click="setNumber(2)">2</button>
        <button @click="setNumber(3)">3</button>
        <button @click="operator = 'add'">&plus;</button>

        <button class="ooo" @click="setNumber(0)">0</button>
        <button @click="calculate">&equals;</button>
      </div>
    </div>
    <footer>Built with love by <a href="https://twitter.com/adesege_">@adesege_</a></footer>
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data() {
    return {
      firstNumber: '',
      secondNumber: '',
      displayValue: 0,
      operator: null,
    };
  },
  methods: {
    setNumber(number) {
      if (!this.operator) {
        this.firstNumber += number;
        this.displayValue = this.firstNumber;
      } else {
        this.secondNumber += number;
        this.displayValue = this.secondNumber;
      }
    },
    calculate() {
      let totalNumber = 0;
      switch (this.operator) {
        case 'add':
          totalNumber = parseFloat(this.firstNumber) + parseFloat(this.secondNumber);
          break;
        case 'subtract':
          totalNumber = parseFloat(this.firstNumber) - parseFloat(this.secondNumber);
          break;
        case 'divide':
          totalNumber = parseFloat(this.firstNumber) / parseFloat(this.secondNumber);
          break;
        case 'multiply':
          totalNumber = parseFloat(this.firstNumber) * parseFloat(this.secondNumber);
          break;
        default: totalNumber = 0;
      }

      this.displayValue = totalNumber || 0;
      this.reset();
    },
    clear() {
      this.reset();
      this.displayValue = 0;
    },
    reset() {
      this.firstNumber = '';
      this.secondNumber = '';
      this.operator = null;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  #calculator {
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    margin: auto;
    max-width: 25rem;
    width: 100%;
    max-height: 34.35rem;
    height: 100%;
    border: 0.0625rem solid #ccc;
    padding: 1rem;

    .title {
      text-align: center;
      margin-top: 0;
      color: lighten($color: #000, $amount: 40);
    }

    &--wrapper---output {
      height: 3.125rem;
      border: 0.0625rem solid #ddd;
      margin-bottom: 1rem;
      display: flex;
      align-items: flex-end;
      justify-content: flex-end;
      padding: 1rem;
    }

    .calculator--wrapper {
      display: grid;

      .calculator-buttons {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(5rem, 1fr));
        grid-gap: 0.5rem;

        button {
          padding: 1em;
          font-size: 1.125rem;
          background-color: #efefef;
          color: #999;

          &:active, &:focus, &:hover {
            background-image: none;
            outline: 0;
            -webkit-box-shadow: none;
            box-shadow: none;
          }
        }

        .cee {
          grid-column-start: 1;
          grid-column-end: 4;
        }

        .ooo {
          grid-column-start: 1;
          grid-column-end: 4;
        }
      }
    }

    footer {
      margin-top: 1.5rem;
      text-align: center;
    }
  }
</style>
