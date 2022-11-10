
<template>
    <div>
        <table class="table ">
            <thead>
                <tr>
                    <th scope="col">Fecha</th>
                    <th scope="col">Positivos</th>
                    <th scope="col">Negativos</th>
                    <th scope="col">Pendientes</th>
                    <th scope="col">Muertes</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in covid">
                    <td>{{ item.Date }}</td>
                    <td>{{ item.Muertes }}</td>
                    <td>{{ item.Negativos }}</td>
                    <td>{{ item.Pendientes }}</td>
                    <td>{{ item.Positivos }}</td>
                </tr>
               
            </tbody>
        </table>
    </div>
</template>

<script lang="ts">
    import  axios  from "axios";
    export default {
        data(){
            return{
                covid:null
            }
        },mounted(){
            this.getCovid();
        },methods:{
            getCovid(){
                axios.get('localhost:3001/coviddaily').then(response =>{
                    console.log(response.data);
                    this.covid = response.data
                }).catch(e=>console.log(e)
                )

            }
        }
    }
</script>

