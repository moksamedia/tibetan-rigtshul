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
  },
  basePath: {
    type: String,
    required: true
  }
})

const {note, styleTibetan, basePath} = props;

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
  return acc
}

if (note.model_name==='LRZTP Colloquial') {
  getSoundFieldMatches('Sound', sounds.value)
  getSoundFieldMatches('Sound Example Sentence', soundsSentence.value)

}
else if (note.model_name==='Tibetan Vocab (Andrew)') {
  getSoundFieldMatches('Sound', sounds.value)
  getSoundFieldMatches('Example Sentence Sound', soundsSentence.value)
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

function getBackText() {
  let result = styleTibetan(note.fields['Back'])
  if (isNotEmptyOrNullString(note.fields['Part of Speech'])) result = `(${note.fields['Part of Speech']}) ` + result
  return result
}

function handlePlaySounds(sound) {
  let URI = "./"+ basePath +"media/" + encodeURIComponent(sound)
  console.log("Playing: " + URI)
  let audio = new Audio(URI);
  audio.play();
}




</script>

<template>
  <v-col cols="12">
    <v-row align="center" justify="start">
      <v-col cols="6" md="3">
        <div class="search-results-front" v-html="styleTibetan(note.fields.Front)"></div>
      </v-col>
      <v-col cols="6" md="auto">
        <div class="search-results-back" v-html="getBackText()"></div>
      </v-col>
      <v-col col="6" md="" >
        <v-btn style="opacity: 0.5;" compact icon="mdi-play" size="x-small" variant="outlined" v-for="(sound, i) in sounds" :key="note.nid + '-sound-' + i" @click="handlePlaySounds(sound)"></v-btn>
        <v-btn  style="opacity: 0.5;" compact icon="mdi-play" size="x-small" variant="outlined" color="warning" v-for="(sound, i) in soundsSentence" :key="note.nid + '-sound-' + i" @click="handlePlaySounds(sound)"></v-btn>
      </v-col>
      <v-col v-if="showDetail" cols="3" md="2" style="text-align: right">
        <v-btn density="compact" size="x-small" variant="plain" @click="showDetail=false">Less</v-btn>
      </v-col>
      <v-col v-else-if="hasMore" cols="3" md="2" style="text-align: right">
        <v-btn density="compact" size="x-small" variant="plain" @click="showDetail=true">More</v-btn>
      </v-col>
    </v-row>
    <v-row v-if="showDetail && note.model_name==='LRZTP Colloquial'" class="lrztp-colloquial detail" no-gutters>
      <v-col>
        <div v-if="note.fields['Note']" v-html="styleTibetan(note.fields['Note'])"></div>
        <div v-if="note.tags">{{'Tags: '+ note.tags}}</div>
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
.v-btn {
  margin-top: 10px;
  margin-right: 10px;
}
</style>
