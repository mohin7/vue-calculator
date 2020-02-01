<template>
  <div class="calculator">
    <div class="display">{{ current || 0 }}</div>
    <div @click="clear" class="ms-btn operator clear">C</div>
    <div @click="sign" class="ms-btn operator">+/-</div>
    <div @click="parcent" class="ms-btn operator">%</div>
    <div @click="devide" class="ms-btn operator">/</div>
    <div @click="append(7)" class="ms-btn">7</div>
    <div @click="append(8)" class="ms-btn">8</div>
    <div @click="append(9)" class="ms-btn">9</div>
    <div @click="times" class="ms-btn operator">*</div>
    <div @click="append(4)" class="ms-btn">4</div>
    <div @click="append(5)" class="ms-btn">5</div>
    <div @click="append(6)" class="ms-btn">6</div>
    <div @click="minus" class="ms-btn operator">-</div>
    <div @click="append(1)" class="ms-btn">1</div>
    <div @click="append(2)" class="ms-btn">2</div>
    <div @click="append(3)" class="ms-btn">3</div>
    <div @click="add" class="ms-btn operator">+</div>
    <div @click="append(0)" class="ms-btn zero">0</div>
    <div @click="dot" class="ms-btn">.</div>
    <div @click="qual" class="ms-btn operator">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      previus: null,
      current: "",
      operator: null,
      operatorClick: false
    };
  },
  methods: {
    clear() {
      this.current = "";
    },
    sign() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    parcent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClick) {
        this.current = "";
        this.operatorClick = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        this.append(".");
      }
    },
    setPrevius() {
      this.previus = this.current;
      this.operatorClick = true;
    },
    devide() {
      this.operator = (a, b) => b / a;
      this.setPrevius();
    },
    times() {
      this.operator = (a, b) => a * b;
      this.setPrevius();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setPrevius();
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPrevius();
    },
    qual() {
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previus)
      )}`;
      this.previus = null;
    }
  }
};
</script>

<style lang="scss" scoped>
.calculator {
  max-width: 800px;
  margin: 0 auto;
  font-size: 50px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  overflow: hidden;
  .display {
    grid-column: 1 / 5;
    background-color: #ddd;
    text-align: right;
    padding: 0 15px;
  }
  .zero {
    grid-column: 1/3;
  }
  .ms-btn {
    user-select: none;
    background-color: #eee;
    cursor: pointer;
    text-align: center;
    border: 1px solid #ddd;
    transition: 0.1s ease-in-out;
    &.operator {
      background-color: #6c5ce7;
      color: #fff;
      &.clear {
        background-color: rgb(68, 51, 196);
        &:hover {
          background-color: #2b1c9c;
        }
      }
      &:hover {
        background-color: rgb(68, 51, 196);
      }
    }
    &:hover {
      background-color: #dde;
    }
  }
}
</style>
