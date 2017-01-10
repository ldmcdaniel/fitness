<style lang="css">
</style>

<template lang="html">
  <div class="col-xs-4">
    <h5>{{options}}</h5>
    <p>{{selected.pull}} at {{pull[selected.pull]}}lbs. for {{reps[week].amrap.pull}} rep</p>
    <p>{{selected.push}} at {{push[selected.push]}}lbs. for {{reps[week].amrap.push}} rep</p>
    <p>{{selected.legs}} at {{legs[selected.legs]}}lbs. for {{reps[week].amrap.legs}} rep</p>
  </div>
</template>

<script>
export default {
  props: [
    'options', 'selected', 'reps', 'pull', 'push', 'legs', 'week',
  ],
};
</script>
