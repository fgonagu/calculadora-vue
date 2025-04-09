<template>
  <div class="display">{{name}}</div>
</template>



<script>
export default {
  props: {
    name: {
      type: String,
      default: "0"
    }
  }
}
</script>



<style scoped>
.display{
  background: whitesmoke;
  text-align: right;
  width: 350px;
  height: 100px;
  padding: 15px;
  border: 6px solid gray;
  font-size: 40px;
  border-radius: 10px;
  overflow: hidden;
  text-overflow: ellipsis;
  direction: rtl;
  box-shadow: 3px 4px rgba(204, 204, 204, 0.8);

}

</style>