<template>
  <div>
    <Liste />
    <ListDone />
  </div>
</template>

<script>
import Liste from "./components/Liste";
import ListDone from "./components/ListDone";

export default {
  name: "App",
  components: {
    Liste,
    ListDone
  },
};
</script>