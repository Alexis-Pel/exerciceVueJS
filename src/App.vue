<template>
  <div>
    <Horloge />
    <Compteur />
    <Liste />
    <ListDone />
  </div>
</template>

<script>
import Compteur from "./components/Compteur";
import Liste from "./components/Liste";
import Horloge from "./components/Horloge";
import ListDone from "./components/ListDone";

export default {
  name: "App",
  components: {
    Compteur,
    Liste,
    Horloge,
    ListDone
  },
};
</script>