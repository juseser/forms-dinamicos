<template>
    <div>
        <v-form @submit.prevent="" class="form d-flex flex-column">
            <span class="message" v-if="!campos.length">No hay campos que mostrar</span>
            <component
                    v-for="(campo,index) in campos" :key="index"
                    :is="campo.etiqueta"
                    :label="campo.label ? campo.label: ''"
                    :type="campo.type ? campo.type : ''"
                    :items="campo.items ? campo.items : ''"
                    v-model="campo.valor"
            >
            </component>
        </v-form>
    </div>
</template>

<script>
    export default{
        props:['campos']
    }
</script>