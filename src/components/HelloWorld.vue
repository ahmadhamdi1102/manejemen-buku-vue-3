<template>
  <div class="container text-center">
    <h1>{{ msg }}</h1>
    <h2>This is my first Vue App</h2>
    <p>My name is {{ name }}</p>
    <input type="text" placeholder="Input your name ..." v-model="name" />
    <button @click="greet(name)">Say Hai..</button>
    <button @click="pass(name)">Send To Manajemen</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      name: "Ahmad",
    };
  },
  props: {
    msg: String,
  },
  methods: {
    greet(name) {
      alert("Haloo ! " + name);
    },
    pass(name) {
      this.$emit("fromChild", name);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  color: rgb(74, 74, 243);
}
</style>
