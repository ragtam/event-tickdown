<template>
  <div class="display-segment--container">
    <h1>{{ character }}</h1>
    <hr style="color: lightblue" />
    <h3>{{ description }}</h3>
  </div>
</template>

<script>
export default {
  props: {
    character: Number,
    description: String,
  },
};
</script>

<style>
.display-segment--container {
  display: inline-block;
  min-width: 120px;
  margin-left: 10px;
  margin-right: 10px;
}

.display-segment--container h1 {
  font-size: 3em;
  line-height: 0px;
  font-weight: 100;
}
</style>
