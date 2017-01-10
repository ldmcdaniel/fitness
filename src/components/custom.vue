<style lang="css">
</style>

<template lang="html">
  <div class="col-lg-4 col-md-4 col-sm-4 col-xs-4">
    <form class="form-horizontal">
      <div class="form-group">
        <div class="row">
          <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6">
            <select v-model="custom.fiveSets.pull" class="form-control">
              <option v-for="(key, value) in pull" :value="value">{{value}}</option>
            </select>
          </div>
          <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
            <h5>{{pull[custom.fiveSets.pull]}}lbs.</h5>
          </div>
          <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
            <h5>{{reps[week].fiveSets.pull}} reps</h5>
          </div>
        </div>
        <div class="row">
          <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6">
            <select v-model="custom.fiveSets.push" class="form-control">
              <option v-for="(key, value) in push" :value="value">{{value}}</option>
            </select>
          </div>
          <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
            <h5>{{push[custom.fiveSets.push]}}lbs.</h5>
          </div>
          <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
            <h5>{{reps[week].fiveSets.push}} reps</h5>
          </div>
        </div>
        <div class="row">
          <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6">
            <select v-model="custom.fiveSets.legs" class="form-control">
              <option v-for="(key, value) in legs" :value="value">{{value}}</option>
            </select>
          </div>
          <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
            <h5>{{legs[custom.fiveSets.legs]}}lbs.</h5>
          </div>
          <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
            <h5>{{reps[week].fiveSets.legs}} reps</h5>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
}
</script>
