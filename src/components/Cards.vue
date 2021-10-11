<template>
  <section class="cards">
    <p class="message" v-if="message != ''">
      {{ message }}
    </p>
    <div v-else class="card" v-for="(item, index) in items" :key="index">
      <audio
        v-if="item.phonetics[0]['audio']"
        :src="'http:' + item.phonetics[0]['audio']"
        controls
      >
        Your browser does not support the audio element.
      </audio>
      <div
        class="card__definitions"
        v-for="(definition, index) in item.meanings[0].definitions"
        :key="index"
      >
        <p class="card__definition">
          <span>Definition: </span> {{ definition["definition"] }}
        </p>
        <p class="card__example" v-if="definition['example']">
          <span>Example: </span> {{ definition["example"] }}
        </p>
        <p class="card__synonyms" v-if="definition['synonyms'].length >= 1">
          <span>Synonym: </span> {{ definition["synonyms"].join() }}
        </p>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({})
export default class Card extends Vue {
  @Prop() private items!: Array<any>;
  @Prop() private message!: "";
}
</script>
