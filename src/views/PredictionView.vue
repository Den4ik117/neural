<template>
  <Header></Header>
  <Menu></Menu>
  <div class="container">
    <section class="block">
        <h2 class="block__title">Нейронная сеть и прогнозирование валюты онлайн</h2>
        <p class="block__paragraph">Будут использоваться последние (windowsize) точки данных в качестве входной информации, в соответствии с вашим настроенным временным окном. Так же наш проект включает в себя среднеквадратическую ошибку (RMSE). Определяет разницу между прогнозируемыми и фактическими значениями, поэтому модель способна учиться, минимизируя ошибку во время тренировочного процесса. За счет Long short-term memory (LSTM) вы сможете более глубоко обучать нейронную сеть, т. к. в отличии от стандартной нейронной сети с прямой связью LSTM имеет соединения обратных связей.</p>
        <p class="block__paragraph">Пример: если вы обучали нейронную сеть ценовыми графиками и ваше временное окно составляет 20, это означает что будет использоваться цена закрытия каждую 20 неделю подряд.</p>
        <p class="block__paragraph">Перед тем как нажать кнопку Make Prediction, вы должны пройти весь путь: подготовить данные, настроить средне-скользящую, обучить и проверить нейронную сеть.</p>
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
