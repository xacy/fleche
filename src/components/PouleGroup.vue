<template>
    <div>
        <h1>Poule nº1</h1>
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
                    <td> {{ fencer.name }}</td>
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
                    <h3>
                        4 fencers <br/> 6 bouts
                    </h3>
                    <table class="table table-sm">
                        <tbody>
                        <tr>
                            <td>1</td>
                            <td>vs</td>
                            <td>4</td>
                        </tr>
                        <tr>
                            <td>Thornton</td>
                            <td>@fat</td>
                        </tr>
                        <tr>
                            <td>Larry the Bird</td>
                            <td>@twitter</td>
                        </tr>
                        </tbody>
                    </table>
                </div>
                <div class="col-sm">
                    <h3>
                        5 fencers <br/> 10 bouts
                    </h3>
                    <div class="row">
                        <div class="col-sm">1</div>
                        <div class="col-sm">-</div>
                        <div class="col-sm">4</div>
                    </div>
                    <div class="row">
                        <div class="col-sm">1</div>
                        <div class="col-sm">-</div>
                        <div class="col-sm">4</div>
                    </div>
                    <div class="row">
                        <div class="col-sm">1</div>
                        <div class="col-sm">-</div>
                        <div class="col-sm">4</div>
                    </div>
                    <div class="row">
                        <div class="col-sm">1</div>
                        <div class="col-sm">-</div>
                        <div class="col-sm">4</div>
                    </div>
                    <div class="row">
                        <div class="col-sm">1</div>
                        <div class="col-sm">-</div>
                        <div class="col-sm">4</div>
                    </div>
                    <div class="row">
                        <div class="col-sm">1</div>
                        <div class="col-sm">-</div>
                        <div class="col-sm">4</div>
                    </div>

                </div>
                <div class="col-sm">
                    <h3>
                        6 fencers <br/> 15 bouts
                    </h3>
                </div>
                <div class="col-sm">
                    <h3>7 fencers <br/> 21 bouts</h3>
                </div>
                <div class="col-sm">
                    <h3>8 fencers <br/> 28 bouts</h3>
                </div>
                <div class="col-sm">
                    <h3>9 fencers <br/> 36 bouts</h3>
                </div>
                <div class="col-sm">
                    <h3>10fencers<br/> 45 bouts</h3>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "PouleGroup",
        props: {
            fencersData: Array
        },
        data(){
            return {
                fencers: this.fencersData
            }
        }
    }
</script>

<style scoped>
    .same{
        background-color: lightgrey;
    }
</style>
