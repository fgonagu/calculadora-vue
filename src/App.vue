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
					console.log('numero'+ value);
					break;
				case '+':
				case '-':
				case '*':
				case '/':
				case '%':
					// llamar a funcion para operadores
					console.log('operador'+ value);
					break;
				case '=':
					// llamar a funcion para igual
					console.log('igual'+ value);
					break;
				case 'AC':
					// llamar a funcion para AC
					console.log('AC'+ value);
					break;
				case 'C':
					// llamar a funcion para C
					console.log('C'+ value);
					break;
				default:
					this.currentInput = "Error"

			}
		},


        fff(value) {
			if(Number(value) >= 0 && Number(value) <= 9 || value === '.') {
                this.memory += this.memoryOp + value;
                this.currentInput += value;
            }

            if(value==='+' || value==='-' || value==='*' || value==='/' || value==='%') {

                this.op = value;
                this.memoryOp = this.op;
                //this.memory +=  this.memoryOp;
                this.currentInput = this.op;

            }

            if (value==='='){
                console.log("memoria al dar al igual: " +this.memory);
                this.result = eval(this.memory).toString();

                console.log("Memoria despues del eval: "+ this.memory);
                console.log("Resultado: "+ this.result);
                this.currentInput = this.result;
            }
            if (value==='AC'){
                console.log("Se ha activado AC");
                this.currentInput = '0';
                this.memory = ' ';
                this.result = ' ';
                this.op = ' ';
                this.memoryOp = ' ';
            }
            if(value==='C'){
                console.log("Se ha activado C");

                if(this.currentInput !== ''){
                    this.currentInput = this.currentInput.slice(0, -1);
                    this.memory = this.currentInput.slice(-1);
                }
                    this.currentInput = '0';
            }
        },
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
