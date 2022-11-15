<script setup>
  import { ref } from 'vue';
  import { saveAs } from 'file-saver';
  import FormularioDinamico from './components/FormularioDinamico.vue';
  
  let campos=ref([]);
  //campos.value=require('./forms/formulario.json')
  campos.value=require('C:/Formularios/formulario.json')
  let label=ref()

  const prueba=(prueba)=>{
      label.value=prueba.label
  }
  
  const cargarCajaTexto=()=>{
    campos.value.push(
      {
        etiqueta: "v-text-field",
        label: "Caja de Texto",
        type: "text",
        class: "cajaTexto",
        requerido:false
      }
    )
  }

  const cargarNumero=()=>{
    campos.value.push(
      {
        etiqueta: "v-text-field",
        label: "Número",
        valor: 123,
        type: "number"
      }
    )
  }

  const cargarCheck=()=>{
    campos.value.push(
      {
        etiqueta: "v-checkbox",
        label: "CheckBox",
        valor: "",
        type: "check"
      }
    )
  }

  const cargarBoton=()=>{
    campos.value.push(
      {
        etiqueta: "v-btn",
        label: "Boton",
        valor: "Botón",
        funcion: "prueba()"
      }
    )
  }

  const cargarRadio=()=>{
    campos.value.push(
      {
        etiqueta: "v-radio",
        label: "Radio",
      }
    )
  }

  const cargarSelect=()=>{
    campos.value.push(
      {
        etiqueta: "v-select",
        label: "Select",
        items:["Test1","Test2","Test3"],
        type: "text",
        valor:"Test1"
      }
    )
  }

  const exportar=(data)=>{
    const formulario = new Blob([JSON.stringify(data)], { type: "text/plain;charset=utf-8" });
    saveAs(formulario, "formulario.json");
  }

</script>

<template>
  <div>
    <v-container>
      <table id="tabla1">
        <tr>
          <td><p>ELEMENTOS DEL FORMULARIO</p></td>
        </tr>
        <tr>
          <td>
            <v-btn width="200" height="50" @click="cargarCajaTexto()">
              <v-icon>mdi-text-box</v-icon>
              Caja de Texto
            </v-btn>
          </td>
        </tr>
        <tr>
          <td>
            <v-btn width="200" height="50" @click="cargarNumero()">
              <v-icon>mdi-numeric</v-icon>
              Numero
            </v-btn>
          </td>
         
        </tr>
        <tr>
          <td>
            <v-btn width="200" height="50" @click="cargarCheck()">
              <v-icon>mdi-checkbox-marked</v-icon>
              CheckBox
            </v-btn>
          </td>
          
        </tr>
        <tr>
          <td>
            <v-btn width="200" height="50" @click="cargarRadio()">
            <v-icon>mdi-radiobox-marked</v-icon>
            Radio
            </v-btn>
          </td>
          
        </tr>
        <tr>
          <td>
            <v-btn width="200" height="50" @click="cargarSelect()">
              <v-icon>mdi-form-dropdown</v-icon>
              Select
            </v-btn>
          </td>
          
        </tr>
        <tr>
          <td> 
            <v-btn width="200" height="50" @click="cargarBoton()"> 
              <v-icon>mdi-send</v-icon>
              Botón
            </v-btn>
          </td>
          
        </tr>
        <tr>
          <td>
            <v-btn width="200" height="50" @click="exportar(campos)">
              <v-icon>mdi-download</v-icon>
              Exportar
            </v-btn>
          </td>
         
        </tr>
      </table>
      <table id="tabla2">
        <tr>
          <td></td>
          <td></td>
          <td>
             <v-app>
              <FormularioDinamico 
                :campos="campos" 
                @prueba="prueba"
              />
            </v-app> 
          </td>
          <td></td>
          <td></td>
        </tr>
      </table>
    </v-container>
    <input type="text" v-model="label"/>
  </div>
</template>

<style>
  /* .cajaTexto{
    background-color: red;
  }  */
  #tabla1{
    width:250px;
    position:relative;
    float: left;
    height: auto;
    margin-right: 10px;
  }

  #tabla1 td{
    height: 60px;
  }

  p{
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-size: 15px;
    font-weight: bold;
  }

  #tabla2{
    /*background-color: darkgray;*/
    border-color: darkgray;
    border-style: outset;
    float: left;
    height: auto;
    position:relative;
    width:900px;
  }
</style>





