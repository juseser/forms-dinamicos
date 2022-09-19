<script setup>
  import { ref } from 'vue';
  import { saveAs } from 'file-saver';
  import FormularioDinamico from './components/FormularioDinamico.vue';
  
  const campos=ref([]);

  const cargarCajaTexto=()=>{
    campos.value.push(
      {
        etiqueta: "v-text-field",
        label: "Caja de Texto",
        valor: "",
        type: "text"
      }
    )
  }

  const cargarNumero=()=>{
    campos.value.push(
      {
        etiqueta: "v-text-field",
        label: "Número",
        valor: "",
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
      }
    )
  }

  const cargarBoton=()=>{
    campos.value.push(
      {
        etiqueta: "v-btn",
        label: "Boton",
        valor: "Botón",
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
      <v-btn width="200" height="50" @click="cargarCajaTexto()">
        <v-icon>mdi-text-box</v-icon>
        Caja de Texto
      </v-btn>
      <v-btn width="200" height="50" @click="cargarNumero()">
        <v-icon>mdi-numeric</v-icon>
        Numero
      </v-btn>
      <v-btn width="200" height="50" @click="cargarCheck()">
        <v-icon>mdi-checkbox-marked</v-icon>
        CheckBox
      </v-btn>
      <v-btn width="200" height="50" @click="cargarRadio()">
        <v-icon>mdi-radiobox-marked</v-icon>
        Radio
      </v-btn>
      <v-btn width="200" height="50" @click="cargarSelect()">
        <v-icon>mdi-form-dropdown</v-icon>
        Select
      </v-btn>
      <v-btn width="200" height="50" @click="cargarBoton()"> 
        <v-icon>mdi-send</v-icon>
        Botón
      </v-btn>
     
      <v-btn width="200" height="50" @click="exportar(campos)">
        <v-icon>mdi-download</v-icon>
      </v-btn>
      <v-app>
        <FormularioDinamico :campos="campos"/>
      </v-app>
    </v-container>
  </div>
</template>




