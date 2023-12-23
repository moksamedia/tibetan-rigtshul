<script setup>

import {ref, toRaw} from 'vue'
import { toRefs, toRef } from 'vue'

const props = defineProps({
  note: {
    type: Object,
    required: true
  },
  styleTibetan: {
    type: Function,
    required: true
  },
  idx: {
    type: Number,
    required: true
  },
  isRandomNotes: {
    type: Boolean,
    default: false
  }
})

const {note, styleTibetan} = props;

let showDetail = ref (false )
let hasMore = ref(false)


const SOUND_REGEX = /\[sound:([^\]]*)\]/g

const sounds = ref([]);
const soundsSentence = ref([]);

function getSoundFieldMatches(fieldName, acc) {
  let matches = [...note.fields[fieldName].matchAll(SOUND_REGEX)]
  for (const match of matches) {
    acc.push(match[1]) // 1 = first capture group
  }
}

if (note.model_name==='LRZTP Colloquial') {
  let soundField = note.fields['Sound']
  let matches = [...soundField.matchAll(SOUND_REGEX)]
  for (const match of matches) {
    sounds.value.push(match[1]) // 1 = first capture group
  }
}
else if (note.model_name==='Tibetan Vocab (Andrew)') {
  let soundField = note.fields['Sound']
  const matches = [...soundField.matchAll(SOUND_REGEX)]
  for (const match of matches) {
    sounds.value.push(match[1]) // 1 = first capture group
  }
}

console.log("sounds=", toRaw(sounds.value))

function isString(str) {
  return (typeof str === 'string' || str instanceof String)
}
function isNotEmptyOrNullString(str) {
  return isString(str) && str !== null && str.trim() !== "";
}

if (note.model_name==='LRZTP Colloquial' && isNotEmptyOrNullString(note.fields['Note'])) {
  hasMore = true
}
else if (note.model_name==='Tibetan Vocab (Andrew)') {
  if (isNotEmptyOrNullString(note.fields['Tense']) ||
      isNotEmptyOrNullString(note.fields['Example Sentence English']) ||
      isNotEmptyOrNullString(note.fields['Example Sentence Tibetan']) ||
      isNotEmptyOrNullString(note.fields['Notes']) ||
      isNotEmptyOrNullString(note.fields['Shesa']) ||
      isNotEmptyOrNullString(note.fields['Synonymous'])
  ) hasMore = true
}

if (sounds.value.length > 0) hasMore = true

function getBackText() {
  let result = styleTibetan(note.fields['Back'])
  if (isNotEmptyOrNullString(note.fields['Part of Speech'])) result = `(${note.fields['Part of Speech']}) ` + result
  return result
}

function handlePlaySounds(sound) {
  let URI = "./rigtshul/media/" + encodeURIComponent(sound)
  console.log("Playing: " + URI)
  let audio = new Audio(URI);
  audio.play();
}




</script>

<template>
  <v-col cols="12">
    <v-row align="center" justify="start">
      <v-col :cols="isRandomNotes ? '4' : 'auto'">
        <div class="search-results-front" v-html="styleTibetan(note.fields.Front)"></div>
      </v-col>
      <v-col>
        <div class="search-results-back" v-html="getBackText()"></div>
      </v-col>
      <v-col v-if="showDetail" cols="auto">
        <v-btn density="compact" size="x-small" variant="plain" @click="showDetail=false">Less</v-btn>
      </v-col>
      <v-col v-else-if="hasMore" cols="auto">
        <v-btn density="compact" size="x-small" variant="plain" @click="showDetail=true">More</v-btn>
      </v-col>
    </v-row>
    <v-row v-if="showDetail && note.model_name==='LRZTP Colloquial'" class="lrztp-colloquial detail" no-gutters>
      <v-col>
        <div v-if="note.fields['Note']" v-html="styleTibetan(note.fields['Note'])"></div>
        <div v-if="note.tags">{{'Tags: '+ note.tags}}</div>
        <v-btn v-for="(sound, i) in sounds" :key="note.nid + '-sound-' + i" @click="handlePlaySounds(sound)">Play</v-btn>
      </v-col>
    </v-row>
    <v-row v-else-if="showDetail && note.model_name==='Tibetan Vocab (Andrew)'" class="tibetan-vocab-andrew detail">
      <v-col>
        <div v-if="note.fields['Tense']" v-html="styleTibetan('Tenses: '+ note.fields['Tense'])"></div>
        <div v-if="note.fields['Example Sentence Tibetan']" v-html="styleTibetan(note.fields['Example Sentence Tibetan'])"></div>
        <div v-if="note.fields['Example Sentence English']" v-html="note.fields['Example Sentence English']"></div>
        <div v-if="note.fields['Notes']" v-html="styleTibetan(note.fields['Notes'])"></div>
        <div v-if="note.fields['Shesa']" v-html="styleTibetan('Shesa: '+ note.fields['Shesa'])"></div>
        <div v-if="note.fields['Synonymous']" v-html="styleTibetan('Synonyms: '+ note.fields['Synonymous'])"></div>
        <div v-if="note.tags">{{'Tags: '+ note.tags}}</div>
      </v-col>
    </v-row>
  </v-col>
</template>

<style scoped>
.detail {
  padding: 20px;
}
.detail div {
  margin-bottom: 10px;
}
</style>
