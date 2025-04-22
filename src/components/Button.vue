<template>
  <button :class="type" @click="handleClick" >
	  {{	buttons	}}
  </button>
</template>


<script>
export default {
  props: {
    buttons: {
      type: String,
      default: "*",

    },
    type: {
      type: String,
      default: 'number',
    }
  }
}


</script>



<style scoped>
button {
  display: flex;
  justify-content: center;
  text-align: center;
  align-items: center;
  border: 0;
  font-size: 30px;
  width: 60px;
  height: 60px;
  border-radius: 10px;
  cursor: pointer;
}
button:hover {
  background-color: rgba(204, 204, 204, 0.6);

}
.number {
  color: darkblue;
  font-weight: bold;
  box-shadow: 3px 4px rgb(165, 163, 163);
}
.operator {
  background: gray;
  color: whitesmoke;
  font-weight: bold;
  box-shadow: 3px 4px rgba(28, 26, 26, 0.6);
}

.equals {
  background: darkblue;
  color: whitesmoke;
  font-weight: bold;
  box-shadow: 3px 4px rgba(91, 156, 230, 0.6);
}

.functionAC {
  font-weight: bold;
  background: red;
  color: whitesmoke;
  box-shadow: 3px 4px rgba(230, 91, 91, 0.6);
}

.functionC {
  width: 130px;
  font-weight: bold;
  background: red;
  color: whitesmoke;
  box-shadow: 3px 4px rgba(230, 91, 91, 0.6);
}
</style>