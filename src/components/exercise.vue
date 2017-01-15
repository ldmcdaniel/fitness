<template lang="html">
  <div class="row">
    <label class="col-xs-2">
      <h5 class="text-right">{{ title }}</h5>
    </label>
    <div class="col-xs-10">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: ['title'],
};
</script>
