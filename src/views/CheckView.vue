<template>
  <Header></Header>
  <Menu></Menu>
  <div class="container">
    <section class="block">
        <h2 class="block__title">Нейронная сеть и прогнозирование валюты онлайн</h2>
        <p class="block__paragraph">Используйте оставшиеся данные для прогнозирования, которые позволят вам увидеть, насколько точны ваши прогнозируемые значения с фактическими ценами.</p>
        <p class="block__paragraph">Примечание: во время работы нейронной сети, окно браузера всегда должно быть открытым.</p>
        <p class="block__paragraph">Чтобы получить более точный прогноз вы должны правильно изучить все настройки. Для каждой котировки, настройки должны быть индивидуальные. Чем точней настройки, тем лучше вы обучите нейронную сеть. Немаловажно правильно рассчитать временное окно, от этого зависят данные которые вы отправите в нейро-сети. Вы можете увеличить или уменьшить количество эпох (Epochs). Пробуйте изменять % размера набора данных Training Dataset Size (%), оставьте 60-70% для обучения, остальные 40-30% будут использоваться для прогноза.</p>
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
