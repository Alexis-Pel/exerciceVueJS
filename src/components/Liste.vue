<template>
  <div>
    <h2>Liste :</h2>
    <input type="text" placeholder="Nom de la tâche" v-model="taskText" />
    <button @click="addToList(taskText)">Ajouter à la liste</button>
    <ul id="liste">
      <li v-for="(item, index) in items" :key="item.message" :id="item.id">
        <p :name="index">
          {{ item.message }}
        </p>
        <input
          type="checkbox"
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
  name: "Liste",
  components: {
  },
  data() {
    return {
      taskText: "",
      items: [],
      listIndex: 0,
    };
  },
  mounted(){
    this.$root.$on('UNDONE', (fitem) => {
      this.addToList(fitem.message)
    })
  },
  methods: {
    check: function (index) {
      this.items[index].done = !this.items[index].done;
      if(this.items[index].done == true){
        this.$root.$emit('TEST', { message: this.items[index].message, id: this.index, done: false })
        this.deleteList(index)
      }
    },
    deleteList: function (index) {
      this.items.splice(index, 1);
    },
    addToList: function (msg) {
      this.items.forEach(element => {
        if(msg == element.message){
          msg+= "_copy"
        }
      });
      this.items.push({ message: msg, id: this.listIndex, done: false });
      this.listIndex++;
    }
  },
};
</script>