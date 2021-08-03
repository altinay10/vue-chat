<script>
export default {
  props: {
    Text,
  },
};
</script>

<template>
  <div class="layout">
    <p>{{ Text }}</p>
  </div>
</template>

<style>
.layout {
  color: black;
  font-size: 18px;
  margin: 15px;
}
</style>