<template>
    <div id="app">
        <header>
            <!-- Fixed navbar -->
            <nav class="navbar navbar-expand-md navbar-dark fixed-top bg-dark">
                <a class="navbar-brand" href="#">Flèche</a>
                <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarCollapse" aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarCollapse">
                    <ul class="navbar-nav mr-auto">
                        <li class="nav-item active">
                            <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#">Fencers</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#">Rules</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link disabled" href="#">Poules</a>
                        </li>
                    </ul>
                    <form class="form-inline mt-2 mt-md-0">
                        <input class="form-control mr-sm-2" type="text" placeholder="Search" aria-label="Search">
                        <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
                    </form>
                </div>
            </nav>
        </header>

        <!-- Begin page content -->
        <main role="main" class="container">
            <h1 class="mt-5">Fencers added</h1>
            <!--<h2>Fencers</h2>
            <fencer-data v-for="fencer in fencers" :key="fencer.id" :fencer="fencer"></fencer-data>-->
            <!--<add-fencer @fencerAdded="fencerAdded"></add-fencer>-->
            <poule-rules></poule-rules>
            <button type="submit" class="btn btn-primary mb-2" @click="distributeFencersInPools">Distribuir</button>
            <!--<poule-group :fencersData="fencers"></poule-group>-->
            <poule-group v-for="(group,index) in poolFencers" :key="index" :fencersData="group" :pouleNumber="index" ></poule-group>
        </main>
    </div>
</template>

<script>
    import AddFencer from './components/AddFencer.vue';
    import FencerData from './components/Fencer.vue';
    import PouleGroup from './components/PouleGroup.vue';
    import PouleRules from './components/PouleRules.vue';

    export default {
        name: 'app',
        components: {
            AddFencer,
            FencerData,
            PouleGroup,
            PouleRules

        },
        data () {
            return {
                msg: 'Welcome to Your Vue.js App',
                fencers: [{id: 1,name: 'Example', club: 1, standing: 'A'},{id: 2,name: 'Example2', club: 2, standing: 'A'},{id: 3,name: 'Example3', club: 1, standing: 'A'}
                    ,{id: 4,name: 'Example4', club: 1, standing: 'B'},{id: 5,name: 'Example5', club: 2, standing: 'A'},{id:6,name: 'Example6', club: 3, standing: 'B'}
                    ,{id: 7,name: 'Example7', club: 1, standing: 'B'},{id: 8,name: 'Example8', club: 2, standing: 'B'},{id: 9,name: 'Example9', club: 3, standing: 'B'}
                    ,{id: 10,name: 'Example10', club: 1, standing: 'C'},{id: 11,name: 'Example11', club: 2, standing: 'C'},{id: 12,name: 'Example12', club: 1, standing: 'C'}

                ],
                poolFencers:[]
            }
        },
        methods:{
            fencerAdded: function ( fencerAdded ) {
                console.log("fencer added "+fencerAdded.name);
                this.fencers.push(fencerAdded);
            },
            distributeFencersInPools(){
                if(this.fencers.length>0){
                    if(this.fencers.length%10==0){
                        this.divideArrayInChunks(10);
                    }
                    else if(this.fencers.length%9==0){
                        this.divideArrayInChunks(9);
                    }
                    else if(this.fencers.length%8==0){
                        this.divideArrayInChunks(8);
                    }
                    else if(this.fencers.length%7==0){
                        this.divideArrayInChunks(7);
                    }
                    else if(this.fencers.length%6==0){
                        this.divideArrayInChunks(6);
                    }
                    else if(this.fencers.length%5==0){
                        this.divideArrayInChunks(5);
                    }
                }
            },
            divideArrayInChunks(poolSize){
                console.log("multiplo de "+poolSize);
                let i=0;
                let divider= Math.floor(this.fencers.length / poolSize);
                let size= this.fencers.length/divider;
                console.log("data: "+size+" - "+this.fencers.length);
                while (i < this.fencers.length) {
                    this.poolFencers.push(this.fencers.slice(i, i += size));
                }

            }
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    h1, h2 {
        font-weight: normal;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
