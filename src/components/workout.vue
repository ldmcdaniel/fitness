<style>
</style>

<template>
  <div class="col-sm-3 col-sm-offset-1 col-xs-offset-2 col-xs-8">
    <form class="form-horizontal">
      <div class="form-group" v-show="settings">
        <exercise :title="'Pull'">
          <select v-model="selected.pull" class="form-control text-left">
            <option v-for="(key, value) in pull" :value="value">{{value}}</option>
          </select>
        </exercise>
        <exercise :title="'Push'">
          <select v-model="selected.push" class="form-control">
            <option v-for="(key, value) in push" :value="value">{{value}}</option>
          </select>
        </exercise>
        <exercise :title="'Legs'">
          <select v-model="selected.legs" class="form-control">
            <option v-for="(key, value) in legs" :value="value">{{value}}</option>
          </select>
        </exercise>
      </div>
      <div class="form-group" v-show="!settings">
        <div class="row">
          <h5>{{option}}</h5>
        </div>
        <div class="row">
          <p>{{selected.pull}} at {{pull[selected.pull]}}lbs. for {{reps[week][scheme].pull}} rep</p>
        </div>
        <div class="row">
          <p>{{selected.push}} at {{push[selected.push]}}lbs. for {{reps[week][scheme].push}} rep</p>
        </div>
        <div class="row">
          <p>{{selected.legs}} at {{legs[selected.legs]}}lbs. for {{reps[week][scheme].legs}} rep</p>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
import exercise from './exercise';

export default {
  data() {
    return {
      legs: {
        Squat: 45,
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
        Deadlift: 45,
        'Bent-over Row': 45,
      },
      selected: {
        pull: 'Pullup',
        push: 'Bench Press',
        legs: 'Squat',
      },
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
    };
  },
  props: ['option', 'settings', 'week', 'scheme'],
  components: { exercise },
};
</script>
