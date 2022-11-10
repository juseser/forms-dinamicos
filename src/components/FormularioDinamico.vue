<script setup>
    defineProps(['campos'])
    const emit=defineEmits(["prueba"])
    
</script>

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
                readonly
                v-model="campo.valor"
                :class="campo.class"
                @click="emit('prueba', campo.type)"
            >
            </component>
        </v-form>
    </div>
</template>

