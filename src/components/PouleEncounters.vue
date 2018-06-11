<template>
    <div class="encounters">
        <h2>Encounters</h2>
        <div class="row">
            <div class="col-sm">
                <h3> {{ number }} Fencers / {{ boutsNumber}} </h3>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "PouleEncounters",
        props: {
            numOfFencers: 0
        },
        data: {
            number: this.numOfFencers
        },
        computed:{
            boutsNumber(){
                return (this.number * (this.number-1))/2;
            }
        }
    }
</script>

<style scoped>

</style>
