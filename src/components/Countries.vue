<template>
  <div class="countries">
    <select @change="$emit('changeCountry', $event.target.value)">
      <option v-for="item in countries" :key="item.label" :value="item.label">
        {{ item.name }}
      </option>
    </select>
  </div>
</template>

<script lang="ts">
import { Component,Vue } from "vue-property-decorator";

@Component
export default class Countries extends Vue {
  data() {
    return {
      countries: [
        { name: "Turkish", label: "tr" },
        { name: "English", label: "en" },
        { name: "German", label: "de" },
        { name: "Spanish", label: "es" },
        { name: "French", label: "fr" },
        { name: "Italian", label: "it" },
        { name: "Russian", label: "ru" },
      ],
    };
  }
}
</script>
