<template>
  <div>
    <input type="text" v-model="mensaje" />
    <div></div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({
    mensaje: "",
  }),

  props: {
    msg: String,
  },

  computed: {
    counterArray() {
      return this.mensaje.length;
    },
  },
  methods: {
    recortado(number) {
      return this.mensaje.repeat(number);
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
