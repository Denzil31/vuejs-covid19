<template>
  <div id="app">
    <div class="table-responsive">
      <table class="table table-hover table-condensed">
        <tr>
          <th>Id</th>
          <th>State</th>
          <th>Indian</th>
          <th>Foreign</th>
          <th>Recovered</th>
          <th>Dead</th>
        </tr>
        <tr v-for="value in msg.data" v-bind:key="value.id">
          <th>{{ value.id }}</th>
          <th>{{ value.state }}</th>
          <th>{{ value.confirmIndian }}</th>
          <th>{{ value.confirmForeign }}</th>
          <th>{{ value.recovered }}</th>
          <th>{{ value.death }}</th>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      msg: ""
    };
  },
  methods: {
    getMessage() {
      const path = "https://covid-19-india-api.herokuapp.com/api";
      axios
        .get(path)
        .then(res => {
          this.msg = res.data;
        })
        .catch(error => {
          console.error(error);
        });
    }
  },
  created() {
    this.getMessage();
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
