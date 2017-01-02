<template>
  <div id="app">
    <h1>Fitness-factory</h1>
    <form>
      <select v-model="currentView">
        <option v-for="(option, key) in options" :value="key">{{option.name}}</option>
      </select>
    </form>
    <div v-show="currentView === 'bigThree'">
      <h3>Warmup</h3>
      <p>Olympic warmup</p>
      <h3>Workout</h3>
      <h5>Part A</h5>
      <p>{{getRandom(pull)}}</p>
      <p>{{getRandom(push)}}</p>
      <p>{{getRandom(legs)}}</p>
      <p>----- ----- -----</p>
      <h5>Part B</h5>
      <p>{{getRandom(pull)}}</p>
      <p>{{getRandom(push)}}</p>
      <p>{{getRandom(legs)}}</p>
    </div>
    <div v-show="currentView === '5x5'">
      <h3>Warmup</h3>
      <p>Olympic warmup</p>
      <h3>Workout</h3>
      <p>{{Object.keys(legs)[0]}} at {{Object.values(legs)[0]}}lbs.</p>
      <p>{{Object.keys(push)[3]}} at {{Object.values(push)[3]}}lbs.</p>
      <p>{{Object.keys(pull)[1]}} at {{Object.values(pull)[1]}}lbs.</p>
      <p>{{Object.keys(push)[2]}} at {{Object.values(push)[2]}}lbs.</p>
      <p>{{Object.keys(legs)[1]}} at {{Object.values(legs)[1]}}lbs.</p>

    </div>
    <div v-show="currentView === 'test'">
      <h3>Warmup</h3>
      <p>Olympic warmup</p>
      <h3>Workout</h3>
      <p>{{Object.keys(legs)[0]}} at {{Object.values(legs)[0]}}lbs.</p>
      <p>{{Object.keys(push)[3]}} at {{Object.values(push)[3]}}lbs.</p>
      <p>{{Object.keys(pull)[1]}} at {{Object.values(pull)[1]}}lbs.</p>
      <p></p>
    </div>
  </div>
</template>

<script>
// import Hello from './components/Hello';

export default {
  data() {
    return {
      options: {
        bigThree: {
          name: 'Push, Pull, and Legs',
        },
        '5x5': {
          name: 'Five rounds of five',
        },
        test: {
          name: 'Judgement time',
        },
      },
      legs: {
        'Barbell Squat': 45,
        'Barbell Deadlift': 45,
        'Barbell Lunge': 45,
        'Barbell Good Morning': 45,
        'Barbell Stright-leg Deadlift': 45,
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
        'Barbell Row': 45,
        'Upright Barbell Row': 45,
      },
      abs: {
        'Toes to Bar': 0,
        'Knees to Chest': 0,
        Situp: 0,
        'Barbell Rollout': 45,
      },
      shoulders: {
        'Side Raise': 0,
      },
      biceps: {
        'Barbell Curl': 45,
      },
      currentView: 'bigThree',
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

    getExercise(name) {
      return name;
    },
  },

  computed: {
    // setCurrentView() {
    //   this.currentView = ;
    // },
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
