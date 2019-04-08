<template>
  <div class="container">
    <p>Post Trucks</p>
    <div class="buttons">
      <a class="button" href="#">
        <img class="icon-play" src="./icon/play.svg">
      </a>
      <div>
        <a class="button modal" href="#" v-b-modal.modal-xl variant="primary">
          <img class="icon-add" src="./icon/add.svg">New
        </a>
        <b-modal id="modal-xl" size="xl">
          <table>
            <tr>
              <th>
                <input type="text" placeholder="Call Controll" v-model="call">
              </th>
              <th>
                <input type="text" placeholder="Read" v-model="read">
              </th>
              <th>
                <input type="text" placeholder="Sound" v-model="sound">
              </th>
              <th>
                <input type="text" placeholder="Truck" v-model="truck">
              </th>
              <th>
                <input type="text" placeholder="Origin" v-model="origin">
              </th>
              <th>
                <input type="text" placeholder="Destination" v-model="destination">
              </th>
              <th>
                <input type="text" placeholder="Pickup" v-model="pickup">
              </th>
              <th>
                <input type="text" placeholder="DH-O" v-model="DO">
              </th>
              <th>
                <input type="text" placeholder="DH-D" v-model="DH">
              </th>
              <th>
                <input type="text" placeholder="F/P" v-model="FP">
              </th>
              <th>
                <input type="text" placeholder="Length" v-model="length">
              </th>
              <th>
                <input type="text" placeholder="Weight" v-model="weight">
              </th>
              <th>
                <input type="text" placeholder="Trip" v-model="trip">
              </th>
              <th>
                <input type="text" placeholder="Alarm" v-model="alarm">
              </th>
              <th>
                <input type="text" placeholder="Action" v-model="action">
              </th>
            </tr>
          </table>
          <button @click="addItem">add</button>
        </b-modal>
      </div>
      <a class="button" href="#">
        <img class="icon-delete" src="./icon/delete.svg" @click="deleteAll">Delete All
      </a>
      <a class="button" href="#">
        <img class="icon-refresh" src="./icon/refresh.svg">Repost All
      </a>
    </div>
    <table>
      <tr>
        <th>Call Controll</th>
        <th>Read</th>
        <th>Sound / Auto Call</th>
        <th>Truck</th>
        <th>Origin</th>
        <th>Destination</th>
        <th>Pickup</th>
        <th>DH-O</th>
        <th>DH-D</th>
        <th>F/P</th>
        <th>Length</th>
        <th>Weight</th>
        <th>Trip</th>
        <th>Alarm</th>
        <th>Action</th>
      </tr>
      <tr class="dynamic-data" v-bind:key="index" v-for="(item, index) of tasks">
          <td>{{ item.call }}</td>
          <td>{{ item.read }}</td>
          <td>{{ item.sound }}</td>
          <td>{{ item.truck }}</td>
          <td>{{ item.origin }}</td>
          <td>{{ item.destination }}</td>
          <td>{{ item.pickup }}</td>
          <td>{{ item.DO }}</td>
          <td>{{ item.DH }}</td>
          <td>{{ item.FP }}</td>
          <td>{{ item.length }}</td>
          <td>{{ item.weight }}</td>
          <td>{{ item.trip }}</td>
          <td>{{ item.alarm }}</td>
          <td>{{ item.action }}</td>
      </tr>
    </table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      call: "",
      read: "",
      sound: "",
      truck: "",
      origin: "",
      destination: "",
      pickup: "",
      DO: "",
      DH: "",
      FP: "",
      length: "",
      weight: "",
      trip: "",
      alarm: "",
      action: "",
      tasks: []
    };
  },
  methods: {
    deleteAll: function() {
        event.preventDefault();
        this.tasks = [];
    },
    addItem: function() {
        const item = {};
        item.call = this.call;
        item.read = this.read;
        item.sound = this.sound;
        item.truck = this.truck;
        item.origin = this.origin;
        item.destination = this.destination;
        item.FP = this.FP;
        item.pickup = this.pickup;
        item.length = this.length;
        item.weight = this.weight;
        item.trip = this.trip;
        item.DO = this.DO;
        item.DH = this.DH;
        item.alarm = this.alarm;
        item.action = this.action;
        item.id = Date.now();
        this.tasks = [...this.tasks, item];
        this.call = "";
        this.read = "";
        this.sound = "";
        this.truck = "";
        this.origin = "";
        this.destination = "";
        this.FP = "";
        this.length = "";
        this.weight = "";
        this.trip = "";
        this.alarm = "";
        this.action = "";
        this.DO = "";
        this.DH = "";
      }
    }
};
</script>
<style>
/* @import 'bootstrap/dist/css/bootstrap.css'; */
/* @import 'bootstrap-vue/dist/bootstrap-vue.css'; */
body {
  background-color: #c6dbeb;
  padding: 10px;
}
.icon-play,
.icon-add,
.icon-delete,
.icon-refresh {
  height: 40px;
  width: 40px;
  padding: 5px;
}
table {
  display: flex;
  flex-direction: column;
  width: 100%;
  color: white;
}
tr {
    display: flex;
    width: 100%;
    border: .5px solid #c6dbeb;;
}
td, th {
  background: #454345;
  padding: 10px;
  flex-grow: 1;
  border-left: .5px solid #fff;
}
.dynamic-data td {
    background-color: white;
    color: black;
    border-right: .5px solid #c6dbeb;
}
.dynamic-data tr {
    border: .5px solid #c6dbeb;
}
p {
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
}
.buttons {
  display: flex;
  flex-direction: row;
}
.buttons a {
  text-decoration: none;
}
.button {
  margin: 5px;
  line-height: 8px;
  padding: 10px;
  font-size: 25px;
}
#modal-xl {
  position: fixed;
  width: 97.6%;
  top: 50% !important;
  left: 50% !important;
  margin-top: -10px;
  margin-left: -665px;
  background-color: #c6dbeb;
  outline: none;
}
#modal-xl input {
  width: 100% !important;
  height: 100% !important;
  border: none;
  outline: none;
  background-color: transparent;
  color: #ffff;
  opacity: 1;
}
#modal-xl td {
  width: 140px;
  height: 40px;
  padding: 10px;
}
</style>
