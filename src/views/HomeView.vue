<template>
  <Header></Header>
  <Menu></Menu>
  <Prediction></Prediction>
</template>

<script>
import Header from "@/components/Header";
import Menu from "@/components/Menu";
import Prediction from "@/components/Prediction";

export default {
  name: "Home",
  components: {
    Prediction,
    Menu,
    Header,
  },
};
</script>
