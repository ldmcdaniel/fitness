<template>
  <div id="app" class="container">
    <div class="row">
      <h1>Fitness-factory</h1>
    </div>
    <div class="row">
      <div class="col-lg-offset-5 col-md-offset-5 col-sm-offset-4 col-xs-offset-3 col-lg-2 col-md-2 col-sm-4 col-xs-6">
        <form class="form-horizontal">
          <div v-show="customExercises">
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
            <div class="form-group">
              <p>or</p>
            </div>
          </div>
          <div class="form-group">
            <button @click.prevent="customExercises = !customExercises" class="btn btn-default">{{setButtonText()}}</button>
          </div>
          <div class="form-group">
            <div class="row">
              <div class="col-lg-4 col-md-4 col-sm-4 col-xs-4">
                <h5>for week</h5>
              </div>
              <div class="col-lg-8 col-md-8 col-sm-8 col-xs-8">
                <select v-model="week" class="form-control">
                  <option v-for="(value, key) in weeks" :value="key">{{key}}</option>
                </select>
              </div>
            </div>

          </div>
        </form>
      </div>
    </div>
    <h3>Warmup</h3>
    <p>Olympic warmup</p>
    <h3>Workout</h3>
    <div class="row" v-show="customExercises">
      <div class="col-xs-4">
        <h5>{{options.amrap}}</h5>
        <p>{{selected.pull}} at {{pull[selected.pull]}}lbs. for {{reps[week].amrap.pull}} rep</p>
        <p>{{selected.push}} at {{push[selected.push]}}lbs. for {{reps[week].amrap.push}} rep</p>
        <p>{{selected.legs}} at {{legs[selected.legs]}}lbs. for {{reps[week].amrap.legs}} rep</p>
      </div>
      <div class="col-xs-4">
        <h5>{{options.fiveSets}}</h5>
        <p>{{selected.pull}} at {{pull[selected.pull]}}lbs. for {{reps[week].fiveSets.pull}} rep</p>
        <p>{{selected.push}} at {{push[selected.push]}}lbs. for {{reps[week].fiveSets.push}} rep</p>
        <p>{{selected.legs}} at {{legs[selected.legs]}}lbs. for {{reps[week].fiveSets.legs}} rep</p>
      </div>
      <div class="col-xs-4">
        <h5>{{options.judgment}}</h5>
        <p>{{selected.pull}} at {{pull[selected.pull]}}lbs. for {{reps[week].judgment.pull}} rep</p>
        <p>{{selected.push}} at {{push[selected.push]}}lbs. for {{reps[week].judgment.push}} rep</p>
        <p>{{selected.legs}} at {{legs[selected.legs]}}lbs. for {{reps[week].judgment.legs}} rep</p>
      </div>
    </div>
    <div class="row" v-show="!customExercises">
      <div class="col-lg-4 col-md-4 col-sm-4 col-xs-4">
        <form class="form-horizontal">
          <div class="form-group">
            <div class="row">
              <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6">
                <select v-model="custom.amrap.pull" class="form-control">
                  <option v-for="(key, value) in pull" :value="value">{{value}}</option>
                </select>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{pull[custom.amrap.pull]}}lbs.</h5>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{reps[week].amrap.pull}} reps</h5>
              </div>
            </div>
            <div class="row">
              <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6">
                <select v-model="custom.amrap.push" class="form-control">
                  <option v-for="(key, value) in push" :value="value">{{value}}</option>
                </select>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{push[custom.amrap.push]}}lbs.</h5>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{reps[week].amrap.push}} reps</h5>
              </div>
            </div>
            <div class="row">
              <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6">
                <select v-model="custom.amrap.legs" class="form-control">
                  <option v-for="(key, value) in legs" :value="value">{{value}}</option>
                </select>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{legs[custom.amrap.legs]}}lbs.</h5>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{reps[week].amrap.legs}} reps</h5>
              </div>
            </div>
          </div>
        </form>
      </div>
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
      <div class="col-lg-4 col-md-4 col-sm-4 col-xs-4">
        <form class="form-horizontal">
          <div class="form-group">
            <div class="row">
              <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6">
                <select v-model="custom.judgment.pull" class="form-control">
                  <option v-for="(key, value) in pull" :value="value">{{value}}</option>
                </select>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{pull[custom.judgment.pull]}}lbs.</h5>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{reps[week].judgment.pull}} reps</h5>
              </div>
            </div>
            <div class="row">
              <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6">
                <select v-model="custom.judgment.push" class="form-control">
                  <option v-for="(key, value) in push" :value="value">{{value}}</option>
                </select>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{push[custom.judgment.push]}}lbs.</h5>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{reps[week].judgment.push}} reps</h5>
              </div>
            </div>
            <div class="row">
              <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6">
                <select v-model="custom.judgment.legs" class="form-control">
                  <option v-for="(key, value) in legs" :value="value">{{value}}</option>
                </select>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{legs[custom.judgment.legs]}}lbs.</h5>
              </div>
              <div class="col-lg-3 col-md-3 col-sm-3 col-xs-3">
                <h5>{{reps[week].judgment.legs}} reps</h5>
              </div>
            </div>
          </div>
        </form>
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
        judgment: 'Judgment time',
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
      custom: {
        amrap: {
          pull: 'Pullup',
          push: 'Bench Press',
          legs: 'Deadlift',
        },
        fiveSets: {
          pull: 'Pullup',
          push: 'Bench Press',
          legs: 'Deadlift',
        },
        judgment: {
          pull: 'Pullup',
          push: 'Bench Press',
          legs: 'Deadlift',
        },
      },
      customExercises: false,
      reps: {
        one: {
          amrap: {
            pull: 1,
            push: 2,
            legs: 3,
          },
          fiveSets: {
            pull: 2,
            push: 6,
            legs: 10,
          },
          judgment: {
            pull: 10,
            push: 21,
            legs: 21,
          },
        },
        two: {
          amrap: {
            pull: 1,
            push: 3,
            legs: 4,
          },
          fiveSets: {
            pull: 3,
            push: 8,
            legs: 13,
          },
          judgment: {
            pull: 13,
            push: 26,
            legs: 26,
          },
        },
        three: {
          amrap: {
            pull: 2,
            push: 3,
            legs: 5,
          },
          fiveSets: {
            pull: 3,
            push: 10,
            legs: 16,
          },
          judgment: {
            pull: 16,
            push: 33,
            legs: 33,
          },
        },
        four: {
          amrap: {
            pull: 2,
            push: 4,
            legs: 6,
          },
          fiveSets: {
            pull: 4,
            push: 12,
            legs: 20,
          },
          judgment: {
            pull: 20,
            push: 41,
            legs: 41,
          },
        },
        five: {
          amrap: {
            pull: 3,
            push: 5,
            legs: 8,
          },
          fiveSets: {
            pull: 5,
            push: 15,
            legs: 26,
          },
          judgment: {
            pull: 26,
            push: 51,
            legs: 51,
          },
        },
        six: {
          amrap: {
            pull: 3,
            push: 6,
            legs: 10,
          },
          fiveSets: {
            pull: 6,
            push: 19,
            legs: 32,
          },
          judgment: {
            pull: 32,
            push: 64,
            legs: 64,
          },
        },
        seven: {
          amrap: {
            pull: 4,
            push: 8,
            legs: 12,
          },
          fiveSets: {
            pull: 8,
            push: 24,
            legs: 40,
          },
          judgment: {
            pull: 40,
            push: 80,
            legs: 80,
          },
        },
        eight: {
          amrap: {
            pull: 5,
            push: 10,
            legs: 15,
          },
          fiveSets: {
            pull: 10,
            push: 30,
            legs: 50,
          },
          judgment: {
            pull: 50,
            push: 100,
            legs: 100,
          },
        },
      },
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

  name: 'app',

  methods: {
    getRandom(exercises) {
      const random = Math.floor(Math.random() * (Object.keys(exercises).length));
      const exercise = Object.keys(exercises)[random];
      const weight = Object.values(exercises)[random];

      return `${exercise}: Use ${weight} lbs.`;
    },
    setButtonText() {
      return this.customExercises ? 'Set Custom Exercises' : 'Set Standard Exercises';
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
