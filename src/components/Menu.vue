<template>
  <nav class="menu">
    <ul class="menu__list">
      <li><router-link to="/" class="menu__link active">Главная</router-link></li>
      <li><router-link to="/neural" class="menu__link">Нейронная сеть</router-link></li>
      <li><router-link to="/neural" class="menu__link">Обучение</router-link></li>
      <li><router-link to="/neural" class="menu__link">Проверка</router-link></li>
      <li><router-link to="/neural" class="menu__link">Создание прогноза</router-link></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "Menu",
};
</script>

<style lang="scss">
.menu {
  background-color: #eab308;

  .menu__list {
    display: flex;
    justify-content: center;
    gap: 20px;
    list-style: none;
  }

  .menu__link {
    display: block;
    padding: 10px 0;
    text-decoration: none;
    color: #a16207;
    transition: 0.3s;

    &:hover {
      color: #713f12;
    }

    &.active {
      color: #713f12;
    }
  }
}
</style>