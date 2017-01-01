<template>
  <div id="app">
    <h1>Fitness-factory</h1>
    <form>
      <select v-model="currentView">
        <option v-for="(option, key) in options" :value="key">{{option.name}}</option>
      </select>
    </form>
    <div v-show="currentView === 'bigThree'">
      <p>{{getRandom(exercises.legs)}}</p>
      <p>{{getRandom(exercises.push)}}</p>
      <p>{{getRandom(exercises.pull)}}</p>
    </div>
    <div v-show="currentView === '5x5'">
      <p>5x5</p>
    </div>
    <div v-show="currentView === 'test'">
      <p>Judgement</p>
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
      exercises: {
        legs: {
          barbellSquat: {
            name: 'Barbell Squat',
            start: 0,
            current: 0,
          },
          airSquat: {
            name: 'Air Squat',
            start: 0,
            current: 0,
          },
          deadlift: {
            name: 'Barbell Deadlift',
            start: 0,
            current: 0,
          },
          lunge: {
            name: 'Barbell Lunge',
            start: 0,
            current: 0,
          },
        },
        push: {
          pushup: {
            name: 'Pushup',
            start: 0,
            current: 0,
          },
          dip: {
            name: 'Dip',
            start: 0,
            current: 0,
          },
          military: {
            name: 'Overhead Press',
            start: 0,
            current: 0,
          },
          bench: {
            name: 'Bench Press',
            start: 0,
            current: 0,
          },
          incline: {
            name: 'Incline Bench Press',
            start: 0,
            current: 0,
          },
        },
        pull: {
          pullup: {
            name: 'Pullup',
            start: 0,
            current: 0,
          },
          row: {
            name: 'Bent Over Row',
            start: 0,
            current: 0,
          },
          upright: {
            name: 'Upright Barbell Row',
            start: 0,
            current: 0,
          },
        },
        abs: {
          toesToBar: {
            name: 'Toes to Bar',
            start: 0,
            current: 0,
          },
          knessToChest: {
            name: 'Knees to Chest',
            start: 0,
            current: 0,
          },
          situp: {
            name: 'Situp',
            start: 0,
            current: 0,
          },
        },
        shoulders: {
          sideRaise: {
            name: 'Side Raise',
            start: 0,
            current: 0,
          },
        },
      },
      currentView: 'bigThree',
    };
  },

  name: 'app',

  methods: {
    getRandom(exercises) {
      const random = Math.floor(Math.random() * (Object.keys(exercises).length));
      const exercise = Object.values(exercises)[random];
      return `${exercise.name}: Use ${exercise.start} lbs.`;
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
