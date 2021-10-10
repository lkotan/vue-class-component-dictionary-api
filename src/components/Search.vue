<template>
  <div class="search">
    <input type="text" autofocus placeholder="Search..." @keyup="$emit('searchEvent',$event.target.value)">
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class Search extends Vue {
}
</script>

<style scoped>

</style>
