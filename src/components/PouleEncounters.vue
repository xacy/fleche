<template>
    <div class="encounters">
        <div class="row">
            <div class="col-sm">
                <h3> {{ number }} Fencers / {{ boutsNumber}} bouts </h3>
            </div>
        </div>
        <table class="table table-sm" v-if="number<=5">
            <thead>
            <tr>
                <th scope="col">Score</th>
                <th scope="col">Left</th>
                <th scope="col"></th>
                <th scope="col">Right</th>
                <th scope="col">Score</th>
            </tr>
            </thead>
            <tr v-for="match in bouts">
                <td></td>
                <td>{{ match.local}}</td>
                <td>-</td>
                <td>{{ match.rival}}</td>
                <td></td>
            </tr>
        </table>
        <table class="table table-sm" v-if="number>5 && number<8">
            <thead>
                <tr>
                    <th scope="col">Score</th>
                    <th scope="col">Left</th>
                    <th scope="col"></th>
                    <th scope="col">Right</th>
                    <th scope="col">Score</th>
                    <th scope="col">Score</th>
                    <th scope="col">Left</th>
                    <th scope="col"></th>
                    <th scope="col">Right</th>
                    <th scope="col">Score</th>
                </tr>
            </thead>
            <tr v-for="i in evenNumbers" >
                <td></td>
                <td>{{bouts[i].local}}</td>
                <td>-</td>
                <td>{{bouts[i].rival}}</td>
                <td></td>
                <td></td>
                <td v-if="bouts[i+1]!=undefined">{{bouts[i+1].local}}</td>
                <td v-if="bouts[i+1]!=undefined">-</td>
                <td v-if="bouts[i+1]!=undefined">{{bouts[i+1].rival}}</td>
                <td></td>
            </tr>
        </table>
        <table class="table table-sm" v-if="number>=8">
            <thead>
                <tr>
                    <th scope="col">Score</th>
                    <th scope="col">Left</th>
                    <th scope="col"></th>
                    <th scope="col">Right</th>
                    <th scope="col">Score</th>
                    <th scope="col">Score</th>
                    <th scope="col">Left</th>
                    <th scope="col"></th>
                    <th scope="col">Right</th>
                    <th scope="col">Score</th>
                    <th scope="col">Score</th>
                    <th scope="col">Left</th>
                    <th scope="col"></th>
                    <th scope="col">Right</th>
                    <th scope="col">Score</th>
                    <th scope="col">Score</th>
                    <th scope="col">Left</th>
                    <th scope="col"></th>
                    <th scope="col">Right</th>
                    <th scope="col">Score</th>
                </tr>
            </thead>
            <tr v-for="i in evenNumbers" >
                <td></td>
                <td>{{bouts[i].local}}</td>
                <td>-</td>
                <td class="borderRight">{{bouts[i].rival}}</td>
                <td></td>
                <td></td>
                <td v-if="bouts[i+1]!=undefined">{{bouts[i+1].local}}</td>
                <td v-if="bouts[i+1]!=undefined">-</td>
                <td class="borderRight" v-if="bouts[i+1]!=undefined">{{bouts[i+1].rival}}</td>
                <td></td>
                <td></td>
                <td v-if="bouts[i+2]!=undefined">{{bouts[i+2].local}}</td>
                <td v-if="bouts[i+2]!=undefined">-</td>
                <td class="borderRight" v-if="bouts[i+2]!=undefined">{{bouts[i+2].rival}}</td>
                <td></td>
                <td></td>
                <td v-if="bouts[i+3]!=undefined">{{bouts[i+3].local}}</td>
                <td v-if="bouts[i+3]!=undefined">-</td>
                <td v-if="bouts[i+3]!=undefined">{{bouts[i+3].rival}}</td>
                <td></td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        name: "PouleEncounters",
        props: {
            numOfFencers: 0
        },
        data() {
            return{
                number: this.numOfFencers,
                bouts: [],
            }
        },
        computed:{
            boutsNumber(){
                //console.log(this.number);
                return (this.number * (this.number-1))/2;
            },
            evenNumbers(){
                let evens=[];
                for(let i=0;i<this.boutsNumber;i++){
                    if(i%2==0 || i==0){
                        evens.push(i);
                    }
                }
                return evens;
            },
            forthMultiple(){
                let evens=[];
                for(let i=0;i<this.boutsNumber;i++){
                    if(i%4==0 || i==0){
                        evens.push(i);
                    }
                }
                return evens;
            }
        },
        methods:{
            boutsOrder(){
                //Formula = n[n+1:tope]
                if(this.number==4){
                    this.bouts=[
                        {local: 1, rival: 4},
                        {local: 2, rival: 3},
                        {local: 1, rival: 3},
                        {local: 2, rival: 4},
                        {local: 3, rival: 4},
                        {local: 1, rival: 2},
                    ]
                }
                else{
                    let fencerBouts=[];
                    for(let initialFencer=1;initialFencer<=this.number;initialFencer++){
                        //console.log("Fencer: "+initialFencer);
                        for(let secondFencer=initialFencer+1;secondFencer<=this.number;secondFencer++){
                            //console.log("vs: "+secondFencer);
                            let temp= {local: initialFencer, rival: secondFencer};
                            //console.log("temp: "+temp.local);
                            fencerBouts.push(temp);
                        }
                    }
                    //console.log("initial : "+fencerBouts.length);
                    //poner todo en un array e ir quitando los que seleccionamos
                    //dejamos fijo el elemento 0
                    //y cogemos uno del array que no tenga ninguno del inmediamante anterior.
                    //salvo el de 4 que es fijo y no se puede aplicar la formula
                    this.bouts.push(fencerBouts[0]);
                    let temp = fencerBouts[0];
                    fencerBouts.splice(0,1);
                    //console.log("second : "+fencerBouts.length);
                    let length = fencerBouts.length;
                    while ( length --){
                        let exitCondition=true;
                        //console.log("length"+length);
                        for(let i =0;i<=length && exitCondition;i++){
                            if(!((temp.local==fencerBouts[i].local || temp.local==fencerBouts[i].rival)
                                || (temp.rival==fencerBouts[i].rival || temp.rival==fencerBouts[i].local))){
                                //console.log("encontrado");
                                this.bouts.push(fencerBouts[i]);
                                temp=fencerBouts[i];
                                fencerBouts.splice(i,1);
                                exitCondition=false;
                            }
                        }
                        if(exitCondition){
                            this.bouts.push(fencerBouts[0]);
                        }
                        else if(length==0){
                            this.bouts.push(fencerBouts[0]);
                        }
                    }
                }
                //console.log("bouts: "+this.bouts.length);
                return this.bouts;
            }
        },
        created() {
            this.boutsOrder();
        }
    }
</script>

<style scoped>
    .borderRight{
        border-right: 1px solid #dee2e6;
    }
</style>
