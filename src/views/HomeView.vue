<template>
  <div class="home">
    <h1>charizard</h1>
    <input type="text" name="" id="" v-model="valor" />
    <button @click="pesquisar(img)">Clique aqui</button>
    <div>
      <img v-show="img" :src="img" alt="" />
    </div>
    <p v-show="name">Nome {{ name }}</p>
    <p v-show="weight">Peso: {{ weight }}kg</p>
    <div v-show="ability">
      Habilidades:
      <p v-for="(ab, key) in ability" :key="key" v-show="ability">
        {{ ab.name }}
      </p>
    </div>
    <p v-show="type" v-for="(tp, key) in type" :key="key">
      {{ tp.name }}
    </p>
  </div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld.vue";
import { prominent } from "color.js";
import { getAverageColor } from "fast-average-color";

export default {
  name: "HomeView",
  data() {
    return {
      valor: null,
      name: null,
      ability: null,
      weight: null,
      img: null,
      weight: null,
      type: null,
    };
  },
  methods: {
    async pesquisar() {
      const req = await fetch(
        `https://pokeapi.co/api/v2/pokemon/${this.valor}`
      );
      const res = await req.json();

      //Passando os valores da api para as variáveis
      this.name = res.name;
      this.ability = res.abilities.map((value) => value.ability);
      this.type = res.types.map((value) => value.type);
      this.weight = res.weight;
      this.img = res.sprites.front_default;
      this.weight = res.weight / 10;

      const color = getAverageColor(res.sprites.front_default);
      console.log(color);
    },
    async pickColor(img) {
      const color = await getAverageColor(img);
      console.log(color);
    },
  },
  components: {
    HelloWorld,
  },
};
</script>

<style scoped>
.home {
  min-height: 200px;
  border-style: solid;
  width: 480px;
  margin: 0 auto;
}
</style>
