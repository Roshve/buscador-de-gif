<template>
  <div>
    <input type="text" v-model="text" />
  </div>
</template>
<script>
export default {
  name: "SearchGif",

  props: {
    text: {
      type: String,
      default: "",
      require: true,
    },
  },
};
</script>
<style scoped>
input {
  height: 30px;
  width: 600px;
  border: 2px solid red;
  border-radius: 4px;
  outline: none;
  padding-left: 10px;
  font-size: 20px;
}

input:focus {
  border-color: blue;
}
</style>