<template>
  <div id="app" class="container">
    <div class="row">
      <h1>Fitness-factory</h1>
    </div>
    <div class="row">
      <div class="col-lg-offset-5 col-md-offset-5 col-sm-offset-4 col-xs-offset-3 col-lg-2 col-md-2 col-sm-4 col-xs-6">
        <form class="form-horizontal">
          <div class="form-group">
            <select v-model="selected.pull" class="form-control">
              <option v-for="(key, value) in pull" :value="value">{{value}}</option>
            </select>
          </div>
          <div class="form-group">
            <select v-model="selected.push" class="form-control">
              <option v-for="(key, value) in push" :value="value">{{value}}</option>
            </select>
          </div>
          <div class="form-group">
            <select v-model="selected.legs" class="form-control">
              <option v-for="(key, value) in legs" :value="value">{{value}}</option>
            </select>
          </div>
        </form>
      </div>
    </div>
      <h3>Warmup</h3>
      <p>Olympic warmup</p>
      <h3>Workout</h3>
      <div class="container">
        <div class="col-xs-4">
          <h5>{{options.amrap}}</h5>
          <p>{{selected.pull}} at {{pull[selected.pull]}}lbs.</p>
          <p>{{selected.push}} at {{push[selected.push]}}lbs.</p>
          <p>{{selected.legs}} at {{legs[selected.legs]}}lbs.</p>
        </div>
        <div class="col-xs-4">
          <h5>{{options.fiveSets}}</h5>
          <p>{{selected.pull}} at {{pull[selected.pull]}}lbs.</p>
          <p>{{selected.push}} at {{push[selected.push]}}lbs.</p>
          <p>{{selected.legs}} at {{legs[selected.legs]}}lbs.</p>
        </div>
        <div class="col-xs-4">
          <h5>{{options.judgement}}</h5>
          <p>{{selected.pull}} at {{pull[selected.pull]}}lbs.</p>
          <p>{{selected.push}} at {{push[selected.push]}}lbs.</p>
          <p>{{selected.legs}} at {{legs[selected.legs]}}lbs.</p>
        </div>
      </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      options: {
        amrap: '20 Minutes AMRAP',
        fiveSets: 'Five rounds',
        judgement: 'Judgement time',
      },
      legs: {
        Squat: 45,
        Deadlift: 45,
        Lunge: 45,
        'Good Morning': 45,
        'Stright-leg Deadlift': 45,
      },
      push: {
        Pushup: 0,
        Dip: 0,
        'Overhead Press': 45,
        'Bench Press': 45,
        'Incline Bench Press': 45,
        'Barbell Push Press': 45,
      },
      pull: {
        Pullup: 0,
        Row: 45,
        'Upright Row': 45,
      },
      abs: {
        'Toes to Bar': 0,
        'Knees to Chest': 0,
        Situp: 0,
        Rollout: 45,
      },
      shoulders: {
        'Side Raise': 0,
      },
      biceps: {
        Curl: 45,
      },
      selected: {
        pull: 'Pullup',
        push: 'Bench Press',
        legs: 'Deadlift',
      },
    };
  },

  name: 'app',

  methods: {
    getRandom(exercises) {
      const random = Math.floor(Math.random() * (Object.keys(exercises).length));
      const exercise = Object.keys(exercises)[random];
      const weight = Object.values(exercises)[random];

      return `${exercise}: Use ${weight} lbs.`;
    },
  },

  computed: {
  },

  components: {
  },
};
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
</style>
