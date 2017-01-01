<template>
  <div id="app">
    <h1>Fitness-factory</h1>
    <form>
      <select v-model="currentView">
        <option v-for="(option, key) in options" :value="key">{{option.name}}</option>
      </select>
    </form>
    <div v-show="currentView === 'amrap'">
      <p>amrap</p>
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
        amrap: {
          name: 'As Many Rounds as Possible',
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
          barbellSquat: 'Barbell Squat',
          airSquat: 'Air Squat',
          deadlift: 'Barbell Deadlift',
          lunge: 'Barbell Lunge',
        },
        push: {
          pushup: 'Pushup',
          dip: 'Dip',
          military: 'Overhead Press',
          bench: 'Bench Press',
          incline: 'Incline Bench Press',
        },
        pull: {
          pullup: 'Pullup',
          row: 'Bent Over Row',
          upright: 'Upright Barbell Row',
        },
        abs: {
          toesToBar: 'Toes to Bar',
          knessToChest: 'Knees to Chest',
          situp: 'Situp',
        },
        shoulders: {
          sideRaise: 'Side Raise',
        },
      },
      currentView: 'amrap',
      selected: '',
    };
  },

  name: 'app',

  methods: {

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
