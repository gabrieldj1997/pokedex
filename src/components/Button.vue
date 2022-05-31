<template>
  <button>{{name}}</button>
</template>

<script>
export default {
  name: "Button",
  props:{
      name: String
  }
};
</script>

<style scoped>
button {
  background: white;
  font-family: inherit;
  padding: 0.6em 1.3em;
  width: 150px;
  font-weight: 900;
  font-size: 12px;
  border: 2px solid black;
  border-radius: 0.6em;
  box-shadow: 0.1em 0.1em;
  margin-top: 5px;
}

button:hover {
  transform: translate(-0.05em, -0.05em);
  box-shadow: 0.15em 0.15em;
  cursor: pointer;
}

button:active {
  transform: translate(0.05em, 0.05em);
  box-shadow: 0.05em 0.05em;
}
</style>