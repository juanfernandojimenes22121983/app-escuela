<script setup>
import { ref } from 'vue';
import AgregarAsignatura from '../components/AgregarAsignatura.vue';
import { useAsignaturasStore } from '../stores/asignaturas';
import { useRouter, RouterLink, RouterView } from 'vue-router';
import DataTable from '../components/DataTable.vue';
import Modal from '../components/profesor/Modal.vue';

const asignaturaStore = useAsignaturasStore();

const router = useRouter();
// validar que exista data en localStorage
if (!localStorage.getItem('data')) {
    router.push('/login');
}

const asignView = ref(false);
const title = ref('Asignatura');

const columns = [
    {data: 'id', title: 'Id'},
    {data: 'nombreAsignatura', title: 'Asignatura'},
    {data: 'cantHoras', title: 'Horas'},
    {data: 'carrera', title: 'Carrera'},
    {data: 'profesor', title: 'Profesor'},
    {data: 'Acciones'}
]
</script>
<template>
    <div>
        <div class="card text-bg-primary p-3 bg-gradient">
            <h1 class="text-center">Asignatura</h1>

        </div>
        <div class="card">
            <div class="card-header">                
                <router-link class="btn btn-primary m-1" to="/agregarAsignatura" @click="asignView = !asignView"> Agregar Asignatura</router-link>
            </div>
            <div class="card-body">

             
                <DataTable :asignaturas="asignaturaStore.asigCarrera" :title="title" :columns="columns" />
            </div>

        </div>
        <!-- componente asignatura -->
        
        <RouterView  v-if="asignView"/>
    </div>
</template>


<style lang="scss" scoped></style>