<template>
  <div class="text-right w-[300px] h-[200px] p-[15px] text-[60px] overflow-hidden text-ellipsis whitespace-nowrap text-white shadow-2xl">{{name}}</div>
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
</style>