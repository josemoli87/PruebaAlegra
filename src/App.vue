<template>
  <div id="app">
    <!-- panel de navegacion -->
    <nav class="navbar navbar-dark bg-info">
      <a href="/" class="navbar-brand">Parqueadero Alégrate</a>
    </nav>
    <!-- pestañas -->
    <ul class="nav nav-pills nav-fill">
      <li class="nav-item">
        <a class="nav-link active border border-dark" href="#">Ingreso</a>
      </li>
      <li class="nav-item">
        <a class="nav-link border border-dark" href="#">Salida</a>
      </li>
      <li class="nav-item">
        <a class="nav-link border border-dark" href="#">Facturación</a>
      </li>
      <li class="nav-item">
        <a class="nav-link border border-dark" href="#">Reportes</a>
      </li>
    </ul>
    <!-- contenido -->
    <div class="container">
      <div class="row mt-4">
        <div class="col-sm-3 text-center">
          <div class="card">
            <div class="card-header">
              <h3>Ingreso de Vehículo</h3>
            </div>
            <div class="card-body">
              <form @submit.prevent="addParking">
                <div class="form-group">
                  <input type="text" class="form-control" v-model="newParking.marca" placeholder="Marca" required>
                </div>
                <div class="form-group">
                  <input type="text" class="form-control" v-model="newParking.placa" placeholder="Placa" required>
                </div>
                <div class="form-group">
                  <span id="liveclock" style="position:absolute;left:0;top:0;"></span>
                </div>
                <button type="submit" class="btn btn-info">Ingresar</button>
              </form>
            </div>
          </div>
        </div>
        <div class="col-sm-8 text-center">
          <!-- <img src="./assets/logo.png"> -->
          <div class="card">
            <div class="card-header">
              <h2>Celdas</h2>
            </div>
            <div class="card-body">
              <div class="container">
                <div class="btn-group btn-group-lg" role="group" aria-label="Basic example">
                  <button type="button" class="btn btn-info border border-primary rounded">C01</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C02</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C03</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C04</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C05</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C06</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C07</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C08</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C09</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C10</button>
                </div>
                <br><br>
                <div class="btn-group btn-group-lg" role="group" aria-label="Basic example">
                  <button type="button" class="btn btn-info border border-primary rounded">C11</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C12</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C13</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C14</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C15</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C16</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C17</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C18</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C19</button>
                  <button type="button" class="btn btn-info border border-primary rounded">C20</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div></div>
    <!-- <router-view/> -->
  </div>
</template>

<script>
import Firebase from "firebase";
import config from "./config.js";
let app = Firebase.initializeApp(config);
let db = app.database();
let parkingRef = db.ref("parking");
export default {
  name: "App",
  firebase: {
    parking: parkingRef
  },
  data() {
    return {
      newParking: {
        marca: "",
        placa: ""
      }
    };
  },
  methods: {
    addParking() {
      parkingRef.push(this.newParking);
      this.newParking.marca = "";
      this.newParking.placa = "";
      this.newParking.hora = "";
    }
  },
  computed: {}
};
</script>

<style>
/* #app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
