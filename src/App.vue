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
                            <a class="nav-link" href="#">Participants</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link disabled" href="#">Pools</a>
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
            <h1 class="mt-5">Participants added</h1>
            <fencer-data v-for="fencer in fencers" v-show="fencers.length>0" :fencer="fencer"></fencer-data>
            <add-fencer @fencerAdded="fencerAdded"></add-fencer>
            <poule-group :fencersData="fencers"></poule-group>
        </main>
    </div>
</template>

<script>
    import AddFencer from './components/AddFencer.vue';
    import FencerData from './components/Fencer.vue';
    import PouleGroup from './components/PouleGroup.vue';
    export default {
        name: 'app',
        components: {
            AddFencer,
            FencerData,
            PouleGroup
        },
        data () {
            return {
                msg: 'Welcome to Your Vue.js App',
                fencers: [{name: 'Example', club: 1, standing: 'A'}]
            }
        },
        methods:{
            fencerAdded: function ( fencerAdded ) {
                console.log("fencer added "+fencerAdded.name);
                this.fencers.push(fencerAdded);
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
