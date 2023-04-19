<template>
  <div class="flex">
    <div class="box">
    </div>
    <input type="text" v-model="color">
  </div>
</template>

<script>
export default {
  data() {
    return {
      color: 'red'
    }
  },
}
</script>

<style scoped>
  .box {
    border: 1px white solid;
    border-radius: 8px 0 0 8px;
    height: 45px;
    width: 40px;
    background: v-bind(color);
    border-right: none;
  }
  input {
    color: white;
    padding: 10px;
    background: black;
    border: 1px white solid;
    border-radius: 0 8px 8px 0;
  }
  input:focus {
    outline: 1px solid transparent;
    outline-offset: 2px;
  }
</style>