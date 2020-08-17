<template>
  <div id="app" class="bg">
    <img alt="Prusicko" class="app-img" src="./assets/prusicko-znak.jpg" />
    <h1 class="header-text">Spotkanie rodzinne na Jedlach już za</h1>
    <display v-bind:dateTo="tickDownDate"></display>

    <div style="height: 60px"></div>

    <span>***</span>
    <h2 class="header-text">Zakończenie lata 2020!</h2>
    <p>29 sierpnia 2020</p>
    <p>start godzina 15</p>

    <div style="height: 60px"></div>

    <div class="footer">
      <img src="./assets/herb.png" />
      <img src="./assets/herb2.png" />
      <img src="./assets/promuje.png" />
      <img src="./assets/marszalek.png" />
    </div>
  </div>
</template>

<script>
import Display from "./components/Display";
import moment from "moment";

export default {
  name: "App",
  components: {
    Display,
  },
  data: function () {
    return {
      tickDownDate: moment("2020 08 29 15:00:00", "YYYY MM DD hh:mm:ss"),
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.app-img {
  height: 180px;
}

.footer {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  background-color: lightblue;
  color: white;
  text-align: center;
  padding-top: 5px;
}

.footer img {
  margin-right: 10px;
  margin-left: 10px;
  height: 100px;
}

@media screen and (max-width: 1024px) {
  #app {
    margin-top: 10px;
  }

  .footer img {
    margin-right: 2px;
    margin-left: 2px;
    height: 40px;
  }

  .app-img {
    height: 100px;
  }

  .header-text {
    margin-top: 0px;
  }
}
</style>
