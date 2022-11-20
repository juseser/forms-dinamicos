<script setup>
  import { ref } from 'vue';
  import { saveAs } from 'file-saver';
  import FormularioDinamico from './components/FormularioDinamico.vue';
  
  let campos=ref([]);
  //campos.value=require('./forms/formulario.json')
  campos.value=require('C:/Formularios/formulario.json')
  let label=ref('Caja de Texto')
  let requerido=ref(true)
  let maxlength=ref(null)
  let tipoInput=ref()
  let type=ref()
  let id=ref()

  const editarCampos=(campo)=>{
      type.value=campo.type
      tipoInput.value=campo.etiqueta
      label.value=campo.label
      requerido.value=campo.requerido
      maxlength.value=campo.maxlength
      id.value=campo.id

      let formulario=document.getElementById('form')
      formulario.addEventListener('submit', function() {
      formulario.reset();
    });
  }
  const cambiarValores=()=>{
    Object.values(campos.value).forEach((campo) => {
        if(campo.id===id.value){
          campo.label=label
        }
    });

  }
  const cargarCajaTexto=()=>{
    campos.value.push(
      {
        id:Date.now(),
        etiqueta: "v-text-field",
        label: label.value,
        type: "text",
        class: "cajaTexto",
        requerido:requerido.value,
        maxlength:maxlength.value
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
                  @editarCampos="editarCampos"
                />
              </v-app> 
          </td>
          <td></td>
          <td></td>
        </tr>
      </table>
    </v-container>
    <div id="tabla3">
      <form action="#" v-show="tipoInput==='v-text-field' && type!='number'" id="form">
        <div><center><label id="titulo"></label></center></div>
        <v-text-field label="Label" v-model="label"></v-text-field>
        <v-checkbox  label="Requerido" v-model="requerido"></v-checkbox>
        <input v-model="id" type="hidden">
        <v-text-field label="Max. Caracteres" v-model="maxlength"></v-text-field>
        <v-btn @click="cambiarValores" color="dark" type="submit"><v-icon>mdi-check-decagram</v-icon>Guardar</v-btn>
      </form>

      <form action="#" v-show="tipoInput==='v-text-field' && type==='number'" id="form">
        <div><center><label id="titulo"></label></center></div>
        <v-text-field label="Label" v-model="label"></v-text-field>
        <v-checkbox  label="Requerido" v-model="requerido"></v-checkbox>
        <v-btn type="submit" class="btn btn-primary boton" id="guardar" color="dark"><v-icon>mdi-check-decagram</v-icon>Guardar</v-btn>
      </form>

      <form action="#" v-show="tipoInput==='v-checkbox'" id="form">
        <div><center><label id="titulo"></label></center></div>
        <v-text-field label="Label" v-model="label"></v-text-field>
        <v-checkbox  label="Requerido" v-model="requerido"></v-checkbox>
        <v-btn type="submit" class="btn btn-primary boton" id="guardar" color="dark"><v-icon>mdi-check-decagram</v-icon>Guardar</v-btn>
      </form>

      <form action="#" v-show="tipoInput==='v-radio'" id="form">
        <div><center><label id="titulo"></label></center></div>
        <v-text-field label="Label" v-model="label"></v-text-field>
        <v-checkbox  label="Requerido" v-model="requerido"></v-checkbox>
        <v-btn type="submit" class="btn btn-primary boton" id="guardar" color="dark"><v-icon>mdi-check-decagram</v-icon>Guardar</v-btn>
      </form>

      <form action="#" v-show="tipoInput==='v-select'" id="form">
        <div><center><label id="titulo"></label></center></div>
        <v-text-field label="Label" v-model="label"></v-text-field>
        <v-checkbox  label="Requerido" v-model="requerido"></v-checkbox>
        <v-btn @click="cambiarValores" color="dark"><v-icon>mdi-check-decagram</v-icon>Guardar</v-btn>
      </form>
    </div>
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
    border-color: darkgray;
    border-style: outset;
    float: left;
    height: auto;
    position:relative;
    width:900px;
  }

  #form{
    background-color: #F1F2F4;
    float: left;
    height: auto;
    position:relative;
    width:550px;
    margin-left: 50px;
    padding: 15px;
  }
</style>





