<template>
    <div>
        <h1>Calculator</h1>
        <div class="container">
            <div class="row">
                <div>
                    <button @click="handlePercentage">%</button>
                    <button @click="handleClearCurrent">CE</button>
                    <button @click="handleClearAll">CL</button>
                    <button @click="handleOperator('/')">/</button>
                </div>
                <div>
                    <button @click="handleInput(7)">7</button>
                    <button @click="handleInput(8)">8</button>
                    <button @click="handleInput(9)">9</button>
                    <button @click="handleOperator('+')">+</button>
                </div>
                <div>
                    <button @click="handleInput(4)">4</button>
                    <button @click="handleInput(5)">5</button>
                    <button @click="handleInput(6)">6</button>
                    <button @click="handleOperator('*')">X</button>
                </div>
                <div>
                    <button @click="handleInput(1)">1</button>
                    <button @click="handleInput(2)">2</button>
                    <button @click="handleInput(3)">3</button>
                    <button @click="handleOperator('-')">-</button>
                </div>
                <div>
                    <button @click="handleInputNegate('negate')">+/-</button>
                    <button @click="handleInput(0)">0</button>
                    <button @click="handleInput('.')">.</button>
                    <button @click="handleTotal">=</button>
                </div>
                <input type="text" v-model="total">
            </div><!-- end of row -->
        </div><!-- end of container -->
    </div>
</template>

<script>
    export default {
        name: 'Calculator',

        data() {
            return {
                total: '',
                operator: '',
                firstValue: '',
                secondValue: ''
            }
        },
        methods: {
            handleInput(val) {
                if (this.operator == '') {
                    this.firstValue += "" + val;
                    this.total = this.firstValue;
                } else {
                    this.secondValue += "" + val;
                    this.total = this.secondValue;
                }
            },
            handleOperator(options) {
                this.operator = options;
            },
            handlePercentage() {
            },
            handleClearCurrent() {
            },
            handleClearAll() {
            },
            handleBackSpace() {
            },
            handleTotal() {
                switch (this.operator) {
                    case "+":
                        this.total = parseFloat(this.firstValue) + parseFloat(this.secondValue);
                        break;
                    case "-":
                        this.total = parseFloat(this.firstValue) - parseFloat(this.secondValue);
                        break;
                    case "*":
                        this.total = parseFloat(this.firstValue) * parseFloat(this.secondValue);
                        break;
                    case "/":
                        this.total = parseFloat(this.firstValue) / parseFloat(this.secondValue);
                        break;
                    default:
                        this.total = 0;
                }

                this.operator = '';
                this.firstValue = this.total;
                this.secondValue = '';

            },
            handleInputNegate() {
            },
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
