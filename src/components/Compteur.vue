<template>
  <div>
    <div>compteur 1 = {{ compteur }} compteur 2 = {{ compteur2 }}</div>
    <button @click="addcomp()">+1 au compteur 1</button>
  </div>
</template>

<script>
export default {
  name: "Compteur",
  data() {
    return {
      compteur: 0,
    };
  },
  computed: {
    compteur2: function () {
      return this.compteur + 1;
    },
  },
  methods: {
    addcomp() {
      this.compteur++;
    },
  },
};
</script>