<template>
  <router-view />
<!--  <div id="nav">-->
<!--    <router-link to="/">Home</router-link> |-->
<!--    <router-link to="/about">About</router-link>-->
<!--  </div>-->
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;500;700;900&display=swap");

*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #f5f5f7;
}

#app {
  font-family: "Roboto", Avenir, Helvetica, Arial, sans-serif;
  font-smoothing: antialiased;
  color: #333;
}

.container {
  max-width: 970px;
  padding: 0 10px;
  margin: 0 auto;
}

.block {
  margin-top: 60px;
  background-color: #fff;
  border-radius: 6px;
  border: 1px solid #6b7280;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}
</style>
