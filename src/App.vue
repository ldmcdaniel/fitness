<style>
</style>

<template>
  <div id="app" class="container">
    <h3 class="text-center">Workout for week {{week}}</h3>
    <div class="row" v-show="settings">
      <div class="col-sm-offset-4 col-sm-2 col-xs-offset-2 col-xs-4">
        <h5 class="text-right">week</h5>
      </div>
      <div class="col-sm-2 col-xs-4">
        <select v-model="week" class="form-control text-left">
          <option v-for="(value, key) in weeks" :value="key">{{value}}</option>
        </select>
      </div>
    </div>
    <div class="row">
      <workout :option="amrap" :settings="settings" :week="week" :scheme="'amrap'"></workout>
      <workout :option="fiveSets" :settings="settings" :week="week":scheme="'fiveSets'"></workout>
      <workout :option="judgment" :settings="settings" :week="week":scheme="'judgment'"></workout>
    </div>
    <div class="row">
      <div class="col-xs-offset-4 col-xs-4">
        <button class="btn btn-success" @click.prevent="settings = !settings">Save and Continue</button>
      </div>
    </div>
  </div>
</template>

<script>
import workout from './components/workout';

export default {
  data() {
    return {
      amrap: '20 Minutes AMRAP',
      fiveSets: 'Five rounds',
      judgment: 'Judgment time',
      settings: false,
      week: 'one',
      weeks: {
        one: 1,
        two: 2,
        three: 3,
        four: 4,
        five: 5,
        six: 6,
        seven: 7,
        eight: 8,
      },
    };
  },
  components: { workout },
};
</script>
