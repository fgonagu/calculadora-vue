<template>
    <div class="body">
        <div class="container">
            <h1>Calculadora</h1>

            <div>
                <Display :name="currentInput"/>
            </div>

            <span>
      Mathematical
    </span>

            <div class="keyboard">
                <Button
                    v-for="(button, index) in buttonList"
                    :key="index"
                    :buttons="button.value"
                    :type="button.type"
                    @button-click="handleButtonClick"


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
    data() {
        return {
            currentInput: "0",
            buttonList: [
                {value: '7', type: 'number'},
                {value: '8', type: 'number'},
                {value: '9', type: 'number'},
                {value: '/', type: 'operator'},
                {value: '%', type: 'operator'},
                {value: '4', type: 'number'},
                {value: '5', type: 'number'},
                {value: '6', type: 'number'},
                {value: 'x', type: 'operator'},
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
        }

    },
    methods: {

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
    font-family: "Courier New";
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
