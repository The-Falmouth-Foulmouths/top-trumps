<!--
<template lang="pug">
  .container
    h1 The Falmouth Foulmouths

    .cards
      .card(v-for="datum in data.profiles" )
        //img(:src=pic)
        span {{getPic(datum)}}
        img(src="https://static.npmjs.com/attachments/ck3uweazy72ye8874y9kkxnx1-gak.png")
        img(:src=getPic(datum))
        .name {{datum.name}}
</template>
-->
<template>
  <div class="container">
    <h1>The Falmouth Foulmouths</h1>
    <div class="cards">
      <div class="card" v-for="datum in data.profiles">
        <div class="name">{{datum.displayName}}</div>
        <img :src="getPic(datum)">
        <div class="skills">
<!--          <div class="skill" >-->
<!--            {{skill.name}}-->
<!--          </div>-->
          <table>
            <tr v-for="skill in datum.skills">
              <td>{{skill.name}}</td>
              <td>{{skill.score}}</td>
            </tr>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue"
import data from "./assets/data.json"
import Juan from "./assets/profilepics/Juan.png"
import Josh from "./assets/profilepics/Josh.png"
import Luis from "./assets/profilepics/Luis.png"
import Oli from "./assets/profilepics/Oli.png"
import Maciej from "./assets/profilepics/Maciej.png"
import Template from "./assets/profilepics/Template.png"

const pics = { Juan, Josh, Luis, Oli, Maciej, Template }

export default Vue.extend({
  data() {
    return {
      data,
    }
  },
  methods: {
    getPic: function (datum) {
      return pics[datum.name]
    }
  }
})
</script>

<style lang="scss" scoped>
.container {
  font-family: "Georgia";
}

h1 {
  margin: 20px;
  color: darkslategray;
}

.card {
  width: 2.5in;
  height: 3.5in;
  background-color: darkseagreen;
  margin: 20px;
  border: 0.1in solid darkslategray;
  border-radius: 0.2in;
  position: relative;
  float: left;

  .name {
    color: darkmagenta;
    font-size: 0.4in;
    text-align: center;
    position: absolute;
    top: 0;
    left: 0;
    padding: 0.05in 0.1in;
    background-color: aliceblue;
    border-radius:0.13in;
  }

  img {
    width: 2.5in ;
    border-radius:0.13in;
    overflow:hidden;
  }

  .skills {
    position: absolute;
    bottom: 0.1in;
    left: 0;
    background-color: darkseagreen;
    height: 1.5in;
    width: 2.5in;
    border-top: 0.1in solid darkslategray;

    table {
      width: 100%;
      height: 100%;
      margin: 0.05in;
      color: darkslategray;
      font-weight: bold;

      tr:nth-child(5) {
        color: honeydew;
        font-weight: bold;
      }
    }
  }
}
</style>