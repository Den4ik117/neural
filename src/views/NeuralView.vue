<template>
  <Header></Header>
  <Menu></Menu>
  <div class="container">
    <section class="block">
        <h2 class="block__title">Нейронная сеть и прогнозирование валюты онлайн</h2>
        <p class="block__paragraph">Мы используем нейронную сеть для прогнозирования фондового рынка и будущие цены акций (валютные пары) на основе исторических данных</p>
    </section>
  </div>
</template>

<script>
import Header from "@/components/Header";
import Menu from "@/components/Menu";
// import Prediction from "@/components/Prediction";

export default {
  name: "Home",
  components: {
    // Prediction,
    Menu,
    Header,
  },
};
</script>
