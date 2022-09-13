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
      <v-btn width="200" height="50" @click="cargarTexto()">
        <v-icon>mdi-alphabetical</v-icon>
        Texto
      </v-btn>
      <v-btn width="200" height="50" @click="exportar()">
        <v-icon>mdi-download</v-icon>
      </v-btn>
      <v-app>
        <FormularioDinamico :campos="campos"/>
      </v-app>
    </v-container>
  </div>
</template>

<script>
  import FormularioDinamico from './components/FormularioDinamico.vue';
    export default{
        name: 'App',
        components:{
          FormularioDinamico
    },
    data(){
      return {
          campos: [
                
          ]
      };
    },
    methods:{
      cargarCajaTexto(){
        if(this.campos.length==0){
          this.campos= [
            {
              etiqueta: "v-text-field",
              label: "Caja de Texto",
              valor: "",
              type: "text"
            }
          ]
        }
        else{
          this.campos.push(
            {
              etiqueta: "v-text-field",
              label: "Caja de Texto",
              valor: "",
              type: "text"
            }
          )
        }
      },
      cargarNumero(){
        if(this.campos.length==0){
          this.campos=[
            {
              etiqueta: "v-text-field",
              label: "Número",
              valor: "",
              type: "number"
            }
          ]
        }
        else{
          this.campos.push(
            {
              etiqueta: "v-text-field",
              label: "Número",
              valor: "",
              type: "number"
            }
          )
        }
      },
      cargarCheck(){
        if(this.campos.length==0){
          this.campos=[
            {
              etiqueta: "v-checkbox",
              label: "CheckBox",
              valor: "",
            }
          ]
        }
        else{
          this.campos.push(
            {
              etiqueta: "v-checkbox",
              label: "CheckBox",
              valor: "",
            }
          )
        }
      },
      cargarBoton(){
        if(this.campos.length==0){
          this.campos=[
            {
              etiqueta: "v-btn",
              label: "Boton",
              valor: "Botón",
            }
          ]
        }
        else{
          this.campos.push(
            {
              etiqueta: "v-btn",
              label: "Boton",
              valor: "Botón",
            }
          )
        }
      }, 
      cargarRadio(){
        if(this.campos.length==0){
          this.campos=[
            {
              etiqueta: "v-radio",
              label: "Radio",
            }
          ]
        }
        else{
          this.campos.push(
            {
              etiqueta: "v-radio",
              label: "Radio",
            }
          )
        }
      },
      cargarSelect(){
        if(this.campos.length==0){
          this.campos=[
            {
              etiqueta: "v-select",
              label: "Select",
              items:["Test1","Test2","Test3"],
              type: "text",
              valor:"Test1"
            }
          ]
        }
        else{
          this.campos.push(
            {
              etiqueta: "v-select",
              label: "Select",
              items:["Test1","Test2","Test3"],
              type: "text",
              valor:"Test1"
            }
          )
        }
      },
      cargarTexto(){
        this.campos.push({
          etiqueta: "v-card-text",
          label: "Texto"
        })
      },
      exportar(){
        console.log(JSON.stringify(this.campos))
      }
    }
  }
</script>


