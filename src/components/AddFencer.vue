<template>
  <div>
    <h1>Add a new fencer</h1>
    <div class="form-group">
      <label for="fencerName">Fencer name: </label>
      <input type="text" class="form-control" id="fencerName" placeholder="Enter fencer name" v-model="fencer.name">
    </div>
    <div class="form-inline">
      <div class="form-group mb-2">
        <label for="fencerClub">Fencer club:</label>
        <select class="form-control" id="fencerClub" v-model="fencer.club">
          <option value="1">VCE</option>
          <option value="2">SAES-BU</option>
          <option value="3">CID-BU</option>
          <option value="4">FECYL</option>
        </select>
      </div>
      <div class="form-group mx-sm-3 mb-2">
        <label for="fencerRating">Example select</label>
        <select class="form-control" id="fencerRating" v-model="fencer.standing">
          <option>A</option>
          <option>B</option>
          <option>C</option>
          <option>D</option>
          <option>E</option>
        </select>
      </div>
      <button type="submit" class="btn btn-primary mb-2" @click="addFencer()">Add fencer</button>
    </div>
  </div>
</template>

<script>
    export default {
        name: "AddFencer",
        data(){
            return{
                fencer: {
                  name: '',
                  club: 1,
                  standing: 'A'
                }
            }
        },
        methods: {
          addFencer () {
            console.log(this.fencer.name);
            this.$emit('fencerAdded', this.fencer);
          }
        }
    }
</script>

<style scoped>

</style>
