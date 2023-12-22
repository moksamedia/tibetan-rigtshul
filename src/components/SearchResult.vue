<script setup>

import {ref} from 'vue'

defineProps({
  note: {
    type: Object,
    required: true
  }
})

let showDetail = ref (false)

</script>

<template>
  <v-row class="search-results" align="center" justify="start">
    <v-col cols="auto">
      <div class="search-results-front" v-html="styleTibetan(note.fields.Front)"></div>
    </v-col>
    <v-col>
      <div class="search-results-back" v-html="styleTibetan(note.fields.Back)"></div>
    </v-col>
    <v-col v-if="showDetail" cols="auto">
      <v-btn density="compact" size="x-small" variant="plain" @click="showDetail = true">More</v-btn>
    </v-col>
    <v-col v-else cols="auto">
      <v-btn density="compact" size="x-small" variant="plain" @click="showDetail = false">Less</v-btn>
    </v-col>
  </v-row>
  <v-row v-if="showDetail" class="search-results-detail">
    <v-col>
      Here is some detail
    </v-col>
  </v-row>
</template>

<style scoped>

</style>
