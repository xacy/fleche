<template>
    <div>
        <h1>Poule nº {{ number}}</h1>
        <table class="table table-bordered table-striped">
            <thead>
                <tr>
                    <th scope="col">Fencer</th>
                    <th scope="col">#</th>
                    <th scope="col" v-for="(fencer, index) in fencers">{{ index +1}}</th>
                    <th scope="col">TS</th>
                    <th scope="col">TR</th>
                    <th scope="col">Ind.</th>
                    <th scope="col">Clas.</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(fencer, index) in fencers">
                    <td> {{ fencer.name }} {{fencer.standing}} {{ fencer.club}}</td>
                    <td> {{ index +1 }} </td>
                    <td v-for="(fencer, intIndex) in fencers" :class="index==intIndex?'same':''">
                        <p v-show="index==intIndex">X</p>
                    </td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                </tr>
            </tbody>
        </table>
        <h2>Encounters</h2>
        <div class="container">
            <div class="row">
                <div class="col-sm">
                    <poule-encounters :numOfFencers="fencersData.length"></poule-encounters>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import PouleEncounters from './PouleEncounters.vue';
    export default {
        components:{
            PouleEncounters
        },
        name: "PouleGroup",
        props: {
            fencersData: Array,
            pouleNumber: Number
        },
        data(){
            return {
                fencers: this.fencersData,
            }
        },
        computed:{
            number(){
                return this.pouleNumber+1;
            }
        }

    }
</script>

<style scoped>
    .same{
        background-color: lightgrey;
    }
</style>
