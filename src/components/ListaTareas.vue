<template>

    <table class="table">
        <thead>
            <tr>
                <th scope="col">#</th>
                <th scope="col">nombre</th>
                <th scope="col">Categoria</th>
                <th scope="col">Estado</th>
                <th scope="col">Numero</th>
                <th scope="col">Accion</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in tareas" :key="item.id">
                <th scope="row">{{item.id}}</th>
                <td>{{item.nombre}}</td>
                <td>
                    <span
                        v-for="(array, index) in item.categorias" :key='index'>

                        {{
                            (item.categorias.length === index + 1) ? array : array + ', '
                        }}
                    </span>
                </td>

                <td>{{item.estado}}</td>
                <td>{{item.numero}}</td>
                <td>
                    <button class="btn btn-danger btn-sm" @click="eliminarTareas(item.id)">
                        Eliminar
                    </button>
                    <router-link
                        class="btn btn-warning ml-2 btn-sm"
                        :to="{
                            name:'Editar',
                            params:{
                                    id: item.id
                            }

                        }"
                    >
                        Editar
                    </router-link>
                </td>


            </tr>
        </tbody>
    </table>
</template>

<script>
import {mapActions, mapState} from 'vuex'

export default {
    computed: {
    ...mapState(['tareas'])

    },
    methods:{
    ...mapActions(['eliminarTareas'])
    }
}
</script>


