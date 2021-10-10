<template>
  <div id="app">
    <h1 class="title">Dictionary API</h1>
    <header>
      <Search @searchEvent="searchEvent" />
      <Countries @changeCountry="changeCountry" />
    </header>
    <Cards :items="items" :message="message"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Search from "./components/Search.vue";
import Countries from "./components/Countries.vue";
import Cards from "./components/Cards.vue";

@Component({
  components: {
    Search,
    Countries,
    Cards,
  },
})
export default class App extends Vue {
  baseURL = "https://api.dictionaryapi.dev/api/v2/entries";
  search = "";
  countryLabel = "tr";
  message = "";
  items: Array<any> = [];

  getData() {
    if (this.countryLabel != "" && this.search != "") {
      fetch(`${this.baseURL}/${this.countryLabel}/${this.search}`)
        .then((res) => res.json())
        .then((data) => {
          if (!Array.isArray(data)) this.message = data.title;
          else {
            this.message = "";
            this.items = data;
          }
        });
    } else this.items = [];
  }
  searchEvent(search: string) {
    this.search = search;
    this.getData();
  }
  changeCountry(countryLabel: string) {
    this.countryLabel = countryLabel;
    this.getData();
  }
}
</script>

<style></style>
