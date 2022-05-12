<template>
  <header class="header">
    <div class="header__title">Neural Network Predictions</div>
    <h1 class="header__subtitle">
      Sunrise ― сайт прогнозирования цены криптовалюты
    </h1>
  </header>
</template>

<script>
export default {};
</script>

<style lang="scss">
.header {
  text-align: center;
  background-image: url(../assets/background.png);
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment: fixed;
  padding: 20px 0;
  font-weight: 700;
  color: #fff;
  display: flex;
  flex-direction: column;
  gap: 10px;

  .header__title {
    font-size: 50px;
    text-transform: uppercase;
  }

  .header__subtitle {
    font-size: 19px;
    text-transform: uppercase;
  }
}
</style>