<template>
    <div>
        <div class="row">
            <div class="col-sm-12">
                <h2>Poule Rules</h2>
            </div>
        </div>
        <div class="row">
            <div class="col-sm-12">
                <p>List of rules to be applied in poule fencers distribution</p>
            </div>
        </div>
        <div class="row">
            <div class="col-sm-12">
                <rule></rule>
            </div>
        </div>
    </div>
</template>

<script>
    import Rule from './Rule.vue';
    export default {
        name: "PouleRules",
        components: {
            Rule
        }
    }
</script>

<style scoped>

</style>
