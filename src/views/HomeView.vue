<template>
  <div class="home">
    <h1>Olá mundo</h1>
    <input type="text" name="" id="" v-model="valor" />
    <button @click="pesquisar()">Clique aqui</button>
    <img v-show="this.img" :src="this.img" alt="" />
    <h1 v-show="this.name">{{ this.name }}</h1>
    <h1 v-show="this.ability">{{ this.ability }}</h1>
  </div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomeView",
  data() {
    return {
      valor: null,
      name: null,
      ability: null,
      weight: null,
      img: null,
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
      this.ability = res.abilities[0].ability.name;
      this.weight = res.weight;
      this.img = res.sprites.front_default;

      console.log(res.weight);
    },
    mostrarConsole() {
      console.log(this.valor);
    },
  },
  components: {
    HelloWorld,
  },
};
</script>


