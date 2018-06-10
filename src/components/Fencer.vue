<template>
  <div class="row">
    <div class="col-sm-6">
      <div class="card" v-show="fencerData!==undefined">
        <div class="card-body">
          <h5 class="card-title">{{ fencerData.name}}</h5>
          <h6 class="card-subtitle mb-2 text-muted">{{ fencerData.club}}</h6>
          <p class="card-text">Standing: {{ fencerData.standing}}</p>
          <!-- add last tournaments links, results etc-->
        </div>
      </div>
    </div>
  </div>

</template>

<script>
    export default {
        name: "Fencer",
        props:{
          fencer: {
            name: String,
            club: String,
            standing: String
          }
        },
      data(){
          return{
            fencerData: this.fencer
          }
      }
    }
</script>

<style scoped>

</style>
