<template>
  <Header></Header>
  <Menu></Menu>
  <div class="container">
    <section class="block">
        <h2 class="block__title">Нейронная сеть и прогнозирование валюты онлайн</h2>
        <p class="block__paragraph">Создается слой рекуррентной нейронной сети (RNN) и в (RNN) добавляется ряд ячеек LSTM. Модель будет обучаться с помощью популярного алгоритма оптимизации для машинного обучения Adam.</p>
        <p class="block__paragraph">Это гиперпараметры (параметры, используемые в процессе обучения), доступные для настройки:</p>
        <p class="block__paragraph">— Training Dataset Size (%): размер обучаемого набора данных. Пример: 70% используем для обучения, а остальные 30% будут использоваться для прогнозирования.</p>
        <p class="block__paragraph">— Epochs: количество раз, когда набор данных используется для обучения модели.</p>
        <p class="block__paragraph">— Learning Rate: Скорость обучения — количество изменения веса во время тренировки на каждом шаге.</p>
        <p class="block__paragraph">— Hidden LSTM Layers: скрытые LSTM-слои для увеличения сложности модели при обучении в многомерном пространстве.</p>
        <p class="block__paragraph">Вы должны настроить гиперпараметры, а затем нажать кнопку «Begin Training Model», чтобы обучить модель.</p>
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
