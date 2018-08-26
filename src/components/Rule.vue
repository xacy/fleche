<template>
    <div>
        <div class="rule">
            It must have <span class="clickable" v-on:click="numberClicked()">{{ number }}</span> fencers of
            <span class="clickable" v-on:click="groupClicked()">{{group.text}}</span> with
            <span class="clickable" v-on:click="groupClicked()">linked category</span>
            per poule
        </div>
        <modal name="numberModal" width="24%" height="auto">
            <div class="card" id="numberCard">
                <div class="card-body">
                    <h5 class="card-title">Number</h5>
                    <h6 class="card-subtitle mb-2 text-muted">Fencers to apply the rule</h6>
                    <select v-model="number">
                        <option v-for="number in numbers" :value="number">{{number}}</option>
                    </select>
                </div>
            </div>
        </modal>
        <modal name="groupModal" width="24%" height="auto">
            <div class="card" id="groupCard">
                <div class="card-body">
                    <h5 class="card-title">Groups</h5>
                    <h6 class="card-subtitle mb-2 text-muted">Categories fencers are divided</h6>
                    <p>Example: a fencer's club, standing, gender...etc.</p>
                    <select v-model="group">
                        <option disabled selected :value="group"> -- select a group -- </option>
                        <option v-for="kind in groups" :value="kind">{{kind.text}}</option>
                    </select>
                </div>
            </div>
        </modal>
    </div>

</template>

<script>
    export default {
        name: "Rule",
        data(){
            return{
                groups: [{id: 1, text: "club"},{id: 2, text: "standing"}],
                numbers: [0,1,2,3,4,5,6,7,8,9,10],
                number: "number",
                group: {id:-1,text: "group"}
            }
        },
        methods: {
            numberClicked(){
                //this.number=0;
                this.$modal.show('numberModal');
            },
            groupClicked(){
                this.$modal.show('groupModal');
            }

        }
    }
</script>

<style scoped>
    .clickable{
        text-decoration: underline cadetblue dashed;
        font-size: 1.3em;
        cursor: pointer;
    }
    .rule{
        margin-bottom:0.5em;
    }
    .v--modal-box .v--modal{
        width:24rem !important;
    }
</style>
