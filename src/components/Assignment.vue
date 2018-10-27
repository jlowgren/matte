<template>
  <div :class="['assignment', { 'assignment--solved': solved }]">
    <span class="assignment__equation">
      {{ firstNumber }} {{ operator }} {{ secondNumber }} =
    </span>
    <input
      ref="input"
      type="number"
      class="assignment__input"
      v-model.number="result"
      :disabled="solved">
  </div>
</template>

<script>
import { Parser } from 'expr-eval';

export default {
  data() {
    return {
      operators: ['+', '-'],
      firstNumber: Math.floor(Math.random() * 9) + 1,
      secondNumber: Math.floor(Math.random() * 9) + 1,
      operator: null,
      result: null,
      solved: false,
    };
  },

  created() {
    this.operator = this.randomOperator();
    this.$nextTick(() => this.$refs.input.focus());
  },

  watch: {
    result(value) {
      const solved = value === this.answer;

      if (solved) {
        this.solved = value === this.answer;
        this.$emit('solved');
      }
    },
  },

  computed: {
    answer() {
      return Parser.evaluate(`x ${this.operator} y`, {
        x: this.firstNumber,
        y: this.secondNumber,
      });
    },
  },

  methods: {
    randomOperator() {
      return this.operators[Math.floor(Math.random() * this.operators.length)];
    },
  },
};
</script>

<style scoped>
/* Remove up/down arrows in number input */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

.assignment {
  position: relative;
  display: flex;
  font-family: Courier, monospace;
  font-size: 2.5rem;
  margin: 1rem 0;
}

.assignment__input {
  width: 100%;
  font-size: inherit;
  font-family: inherit;
  background: #329a37;
  color: #333;
  border: 0;
}

.assignment__equation {
  font-family: 'Chalkduster', Helvetica, sans-serif;
  display: inline-block;
  margin-right: 1rem;
  white-space: nowrap;
}

/* Styling for a correctly answered assignment */
.assignment--solved .assignment__input {
  background-color: lightgreen;
}

.assignment--solved::after {
  content: "👍";
  display: block;
  position: absolute;
  top: 0.125rem;
  right: 1rem;
  animation: rotate 0.5s infinite alternate linear;
  transform: rotate(-10deg);
}

/* Animation */
@keyframes rotate {
  100% {
    transform: rotate(10deg);
  }
}
</style>
