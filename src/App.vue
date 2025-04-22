<template>
    <div class="body">
        <div class="container">
            <h1>
				Calculadora
			</h1>
			<Display :name="currentInput"/>
            <span>
      			Mathematical
    		</span>
			<div class="keyboard">
				<Button
					v-for="(button, index) in buttonList"
					:key="index"
					:buttons="button.value"
					:type="button.type"
					@click="handleButtonClick(button.value)"
				/>
			</div>
        </div>
    </div>
</template>

<script>
import Display from './components/Display.vue';
import Button from './components/Button.vue';


export default {
    components: {
        Display,
        Button,
    },
    data: () => ({
        op: "",
        result: "",
        memory: "",
        memoryOp: "",
        currentInput: "",
        lastOperator: false,
        buttonList: [
            {value: '7', type: 'number'},
            {value: '8', type: 'number'},
            {value: '9', type: 'number'},
            {value: '/', type: 'operator'},
            {value: '%', type: 'operator'},
            {value: '4', type: 'number'},
            {value: '5', type: 'number'},
            {value: '6', type: 'number'},
            {value: '*', type: 'operator'},
            {value: '-', type: 'operator'},
            {value: '1', type: 'number'},
            {value: '2', type: 'number'},
            {value: '3', type: 'number'},
            {value: '+', type: 'operator'},
            {value: '=', type: 'equals'},
            {value: '0', type: 'number'},
            {value: '.', type: 'number'},
            {value: 'AC', type: 'functionAC'},
            {value: 'C', type: 'functionC'},
        ],
    }),
    methods: {
        handleButtonClick(value) {
            switch (value) {
                case '0':
                case '1':
                case '2':
                case '3':
                case '4':
                case '5':
                case '6':
                case '7':
                case '8':
                case '9':
                    // llamar a funcion para numeros
                    this.numbers(value);
                    break;
                case '+':
                case '-':
                case '*':
                case '/':
                case '%':
                    // llamar a funcion para operadores
                    this.operators(value);
                    break;
                case '=':
                    // llamar a funcion para igual
                    this.equals();
                    break;
                case 'AC':
                    // llamar a funcion para AC
                    this.clearAll();
                    break;
                case 'C':
                    // llamar a funcion para C
                    this.clearLast();
                    break;
                case '.':
                    //llamar a funcion decimal
                    this.decimal();
                    break;
                default:
                    this.currentInput = "Error"

            }
        },
        numbers(value) {
            if (this.lastOperator) {

                this.memory += this.op;
                this.lastOperator = false;
                this.currentInput = "";
            }
            this.currentInput += value;
        },
        operators(value) {
            if (!this.lastOperator && this.currentInput !== "") {
                this.memory += this.currentInput;
                this.currentInput = "";
            }
            this.op = value;
            this.lastOperator = true;
            this.currentInput = value;
        },
        equals() {
            if (!this.lastOperator) {
                this.result = eval(this.memory + this.currentInput);
                this.currentInput = this.result.toString();
            }
            this.memory = "";

        },
        clearAll() {
            this.currentInput = "";
            this.memory = "";
            this.lastOperator = false;
        },
        clearLast() {
            this.currentInput = this.currentInput.slice(0, -1);
            this.currentInput = this.currentInput === "" ? "0" : this.currentInput;

        },
        decimal() {
            this.currentInput += ".";
        }
    }
}

</script>
<style scoped>
* {
    box-sizing: border-box;
}

.body {
    margin: 0;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;

}

.container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    gap: 5px;
    height: 560px;
    border: 4px solid darkblue;
    background: lightblue;
    border-radius: 10px;
    padding: 15px;
    box-shadow: 6px 4px rgba(128, 128, 128, 0.4);

}

h1 {
    color: darkblue;
    font-family: "Courier New", Courier, monospace;
    font-size: 30px;
    text-decoration: underline;

}

span {
    display: flex;
    color: rgba(128, 128, 128, 0.5);
    padding-left: 15px;
    padding-top: 5px;
    align-self: flex-start;

}

.keyboard {
    display: grid;
    grid-template-columns: repeat(5, 60px);
    border: 0;
    padding: 15px;
    gap: 10px;
}

</style>
