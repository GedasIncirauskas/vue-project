<template>
  <button @click="onClick()" class="button-style">{{ name }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    name: String,
  },
  methods: {
    onClick() {
      this.$emit("toggle-add");
    },
  },
};
</script>

<style scoped>
.button-style {
  display: inline-block;
  background: rgb(0, 0, 0);
  color: rgb(232, 232, 232);
  border: none;
  padding: 0.5rem 2rem;
  margin: 0.5rem;
  border-radius: 0.5rem;
  cursor: pointer;
  text-decoration: none;
  font-size: 1rem;
}
.button-style:focus {
  outline: none;
}
.button-style:active {
  transform: scale(0.98);
}
.button-style-block {
  display: block;
  width: 100%;
}
</style>
