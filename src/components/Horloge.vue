<template>
  <div id="horloge" style="display: flex; justify-content: center">
    <span>{{ horloge }}</span>
  </div>
</template>

<script>
export default {
  name: "Horloge",
  data() {
    return {
      now: new Date(),
      intervalID: null,
    };
  },
  computed: {
    horloge: function () {
      var hour = this.now.getHours();
      var minutes = this.now.getMinutes();
      var seconds = this.now.getSeconds();
      return `${hour} : ${minutes} : ${seconds}`;
    },
  },
  beforeMount() {
    (this.intervalID = setInterval),
      setInterval(() => {
        this.now = new Date();
      }, 1000);
  },
};
</script>