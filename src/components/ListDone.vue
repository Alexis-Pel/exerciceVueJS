<template>
  <div>
    <h2>Tâches effectuées</h2>
    <ul id="listeDone">
      <li v-for="(item, index) in itemsDone" :key="item.message" :id="item.id">
        <p
          v-if="item.done"
          v-bind:style="{ textDecoration: 'line-through' }"
          :name="index"
        >
          {{ item.message }}
        </p>
        <input
          type="checkbox"
          :value="index"
          v-model="item.done"
          @click="check(index)"
        />
        <label for="checkbox">Done</label>
        <button @click="deleteList(index)">Supprimer</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ListDone",
  data() {
    return {
      itemsDone: [],
    };
  },
  mounted() {
    this.$root.$on("TEST", (msg) => {
      this.itemsDone.push(msg);
      this.check(this.itemsDone.indexOf(msg));
    });
  },
  methods: {
    check: function (index) {
      this.itemsDone[index].done = !this.itemsDone[index].done;
      if (!this.itemsDone[index].done) {
        this.$root.$emit("UNDONE", {
          message: this.itemsDone[index].message,
          id: this.index,
          done: false,
        });
        this.deleteList(index)
      }
    },
    deleteList: function (index) {
      this.itemsDone.splice(index, 1);
    },
  },
};
</script>

<style>
</style>