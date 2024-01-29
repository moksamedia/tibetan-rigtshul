<script>
import grammarCards from './assets/grammar-cards.csv'
import notesJson from './assets/notes.json'

const tagsSet = notesJson.reduce((acc, curr) => {
  curr.tags.forEach(tag => acc.add(tag))
  return acc
}, new Set())

const tagsSorted = Array.from(tagsSet).sort()

console.log("tags=",tagsSorted)

const decksSet = notesJson.reduce((acc, curr) => {
  curr.decks.forEach(deck => acc.add(deck.name))
  return acc
}, new Set())

const decksSorted = Array.from(decksSet).sort()

console.log("decks=",decksSorted)

const grammarLessonSet = grammarCards.reduce((acc, curr) => {
  if (curr.Lesson) acc.add(curr.Lesson)
  return acc
}, new Set())

const grammarLessonSetSorted = Array.from(grammarLessonSet).sort()

console.log("grammarLessonSetSorted=",grammarLessonSetSorted)



const sampleSize = ([...arr], n = 1) => {
  let m = arr.length;
  while (m) {
    const i = Math.floor(Math.random() * m--);
    [arr[m], arr[i]] = [arr[i], arr[m]];
  }
  return arr.slice(0, n);
};

function rand(array) { return array[Math.floor(Math.random() * array.length)] };

const firstPerson = [
  'ང་',
  'ང་ཚོ་',
  'རང་',
  'ང་རང་',
  'ང་གཉིས་',
  'ང་དང་རོགས་པ་དེ་མཉམ་དུ་',
  'ང་ཚོ་ཚང་མ་',
  'ང་ཚོ་གསུམ་'
]

const secondPerson = [
  'ཁྱེད་རང་',
  'ཁྱེད་རང་ཚོ་',
  'ཁྱོད་',
  'ཁྱོད་རྣམ་',
  'ཁྱོད་རྣམ་ཚོ་',
  'ཁྱོད་རྣམ་པ་ཚོ་',
  'ཁྱེད་རང་ཚོ་ཚང་མ་',
  'ཁྱེད་རང་གཉིས་',
  'ཁྱེད་རང་གསུམ་'
]

const thirdPerson = [
  'ཁོང་',
  'ཁོང་ཚོ་',
  'བཀྲ་ཤིས་',
  'མི་མང་ཆེ་བ་',
  'མོ་ལགས་',
  'ཁོ་',
  'ཁོང་གི་ཁང་བདག་',
  'ལྷ་མོ་',
  'ཁོང་གི་གྲོགས་པོ་',
  'སློབ་ཕྲུག་དེ་',
  'རྨོ་རྨོ་ལགས་',
  'ངའི་ཇོ་ཇོ་ལགས་',
  'རྒན་ལགས་',
  'རིན་པོ་ཆེ་དེ་ཚོ་ལགས་',
  'རྫ་མཁན་རྣམས་',
  'ཨ་ཅག་ལགས་',
  'སྐུ་གཞོགས་ལགས་',
  'སྒྲོལ་མ་',
  'ངའི་ཨ་ཁུ་',
  'ཁྱེད་རང་ཀྱི་ཨ་མ་ལགས་',
  'རྒྱ་གར་བ་ཚོ་',
  'བོད་པ་དེ་',
  'སློབ་ཕྲུག་ཆེན་མོ་བ་',
  'བོད་ཡིག་དགེ་རྒན་',
]

const past = [
  'སྔོན་མ་',
  'ཁ་སང་',
  'དེ་རིང་སྔོན་ལ་',
  'བདུན་ཕྲག་སྔོན་མ་',
  'དེ་རིང་ཞོགས་པ་',
  'གཟའ་འཁོར་སྔོན་མ་ལ་',
  'བདང་དགོང་',
  'ཆུང་དུས་',
  'ཁ་ས་དགོང་དག་',
  'ཁ་སིང་',
  'ལོ་སྔོན་མར་',
  'སྔོན་མར་',
  'ཆུང་ཆུང་སྐབས་ལ་',
  'གཟའ་པ་སངས་སྔོན་མ་ལ་',
  'ལོ་ཁ་ཤེས་སྔོན་ལ་',
  'གཟའ་མཇུག་སྔོན་མར་',
  'ལོ་ཁ་ཤས་ཀྱི་སྔོན་ལ་',
  'ཁེ་ས་དགོང་དག་',
  'མདང་དགོང་',
  'ན་ནིང་'
]

const present = [
  'ད་ལྟ་',
  'དེང་སང་',
  'ཉེ་ཆར་',
  'ནན་རྒྱུན་',
  'ཉིན་ལྟར་',
  'ཉི་མ་ཉིན་གང་',
  'ལོ་ལྟར་རེད་བཞིན་',
  'ད་ལྟ་ལམ་སང་',
  'ད་ལྟ་རང་',
  'ད་རེས་',
  'སྤྱིར་བཏང་',
]

const future = [
  'སང་ཉིན་',
  'མ་འོངས་པར་',
  'དོ་དགོང་',
  'གནངས་ཉིན་ཀ་',
  'གནངས་ཉིན་',
  'གཞེས་ཉིན་',
  'ཉིན་མ་གཅིག་',
  'དེ་རིང་དགོང་དག་',
  'སང་ཉིན་ཞོགས་གས་',
  'གཟའ་ཟླ་བ་རྗེས་མ་ལ་',
  'གཟའ་པ་སངས་རྗེས་མ་ལ་',
  'དགུན་ཁ་རྗེས་མ་སྐབས་ལ་',
  'གཟའ་མཇུག་རྗེས་མར་',
  'རྗེས་ལ་',
  'དུས་ཚོད་སྟོང་པ་རག་ན་',
  'གུང་སེང་གི་སྐབས་ལ་',
  'ཏོག་ཙམ་རྗེས་ལ་',
  'ཉིན་གསུམ་་རྗེས་ལ་',
  'སང་དགོང་',
  'ལོ་འདི་རྗེས་ལ་'
]

const posNeg = [
  'positive',
  'negative'
]

const aspect = [
  'direct/immediate',
  'general/habitual'
]

const questionStatement = [
  'statement',
  'question'
]

const permutations2 = [
  {tense:'past', questionStatement:'statement', posNeg:'positive', person: '1st', aspect: ''},
  {tense:'past', questionStatement:'statement', posNeg:'negative', person: '1st', aspect: ''},
  {tense:'past', questionStatement:'statement', posNeg:'positive', person: '1st', aspect: ''},
  {tense:'past', questionStatement:'statement', posNeg:'negative', person: '1st', aspect: ''},
  {tense:'present', questionStatement:'statement', posNeg:'positive', person: '1st', aspect: 'habitual'},
  {tense:'present', questionStatement:'statement', posNeg:'positive', person: '1st', aspect: 'immediate'},
  {tense:'present', questionStatement:'statement', posNeg:'negative', person: '1st', aspect: ''},
  {tense:'present', questionStatement:'statement', posNeg:'negative', person: '1st', aspect: ''},

]
</script>
<script setup>
import {ref, onMounted, unref, toRaw} from 'vue'
import { useDisplay } from 'vuetify'
import SearchResult from './components/SearchResult.vue'

const { width, mobile } = useDisplay()

let searchTerm = ref('')
let searchResults = ref([])
let randomNotes = ref([])
let randomGrammarCards = ref([])
let permutations = ref([])
let allPermutations = ref([])
let timeAndPersonPermutations = ref([])
let personAndTimeForDrilling = ref({})
let randomFilterByTags = ref([])
let numRandomWords = ref(20)
let grammarFilterByLesson = ref([])

function onSearchTermChange() {
  if (searchTerm.value == null || searchTerm.value.trim() === "") {
    searchResults.value = [];
  }
  else {
    searchResults.value = notesJson.filter(noteJson => {
      let front = noteJson.fields.Front
      let back = noteJson.fields.Back
      return (front && front.includes(searchTerm.value)) || (back && back.includes(searchTerm.value))
    })
    console.log("Found: " + searchResults.value.length)
  }
}

function random_personAndTimeForDrilling() {
  personAndTimeForDrilling.value = {
    past: rand(past),
    present: rand(present),
    future: rand(future),
    firstPerson: rand(firstPerson),
    secondPerson: rand(secondPerson),
    thirdPerson: rand(thirdPerson),
  }
}

function random_timeAndPersonPermutations() {
  let _past = rand(past)
  let _present = rand(present)
  let _future = rand(future)
  timeAndPersonPermutations.value =  [
    {tense:'PAST', tenseText: `${_past} ${rand(firstPerson)}`},
    {tense:'PAST', tenseText: `${_past} ${rand(secondPerson)}`},
    {tense:'PAST', tenseText: `${_past} ${rand(thirdPerson)}`},
    {tense:'PRESENT', tenseText: `${_present} ${rand(firstPerson)}`},
    {tense:'PRESENT', tenseText: `${_present} ${rand(secondPerson)}`},
    {tense:'PRESENT', tenseText: `${_present} ${rand(thirdPerson)}`},
    {tense:'FUTURE', tenseText: `${_future} ${rand(firstPerson)}`},
    {tense:'FUTURE', tenseText: `${_future} ${rand(secondPerson)}`},
    {tense:'FUTURE', tenseText: `${_future} ${rand(thirdPerson)}`},
  ]
}

function noteContainsTag(note, filterTags) {
  //console.log("filterTags:", filterTags)
  //console.log("note.tags:", note.tags)
  for (let i=0;i<filterTags.length;i++) {
    //console.log("Plunk")
    if (note.tags.includes(filterTags[i])) {
      //console.log(`note.tags:${note.tags} includes ${filterTags[i]}`)
      return true
    }
    else {
      //console.log(`note.tags:${note.tags} DOES NOT include ${filterTags[i]}`)
    }
  }
  return false
}

function compareNotes(a,b) {
  return a.fields['Part of Speech'] < b.fields['Part of Speech']
}

function random_notes(numRandomWords) {
  let filtered = notesJson
  let filterTags = toRaw(randomFilterByTags.value)
  //console.log("filterTags", filterTags)
  if (filterTags.length > 0) {
    filtered = notesJson.filter(note => {
      return noteContainsTag(note, filterTags)
    })
  }
  randomNotes.value = sampleSize(filtered, numRandomWords.value).sort(compareNotes)
  console.log("randomNotes=",randomNotes.value)
}

function random_grammarCard(numRandomWords) {
  let filtered = grammarCards
  let rawFilterLessons = toRaw(grammarFilterByLesson.value)
  if (rawFilterLessons.length > 0) {
    filtered = grammarCards.filter(card => rawFilterLessons.includes(card.Lesson))
  }
  randomGrammarCards.value = sampleSize(filtered, numRandomWords.value)
}

function random_allPermutations() {
  random_timeAndPersonPermutations()
  permutations.value = questionStatement.flatMap(a => posNeg.map(c => {return {questionStatement:a, 'posNeg': c}}))
  allPermutations.value = timeAndPersonPermutations.value.flatMap(d => permutations.value.map(v => {return {...v,...d}}))
}

function randomize() {
  random_personAndTimeForDrilling()
  random_notes(numRandomWords)
  random_grammarCard(numRandomWords)
  random_timeAndPersonPermutations()
  random_allPermutations()
}

function isString(test) {
  return typeof text !== 'string' || text instanceof String
}

function processTibetan(text, style, _class) {
  return text.replace(/[\u0F00-\u0FFF]+/gm, (match) => {
    return `<span style="${style}" class="${_class}">${match}</span>`
  })
}

function styleTibetan(text) {
  if (text == null || !isString(text) || text.trim() === "") return text;
  return processTibetan(text, null, "tibetan")
}


function styleTibetanSmaller(text) {
  if (text == null || !isString(text) || text.trim() === "") return text;
  return processTibetan(text, null, "tibetan-smaller")
}

let showSearchResultsDetail = ref(new Set())

const currentUrl = window.location.href;
console.log(currentUrl);
const basePath = ''
if (currentUrl.includes('localhost')) {
  let basePath = "rigtshul/"
}

function showLessonPdf(card) {
  let URI = "./"+basePath+"pdf/" + encodeURIComponent('LRZTP 9 ' + card.Lesson + ".pdf")
  console.log("Opening: " + URI)
  window.open(URI, '_blank')
}

onMounted(() => {
  randomize(),
      mobile,
      width
})

</script>

<template>
  <main>
    <v-container>
      <v-row>
        <v-col cols="6" md="">
          <v-btn @click="randomize">
            Randomize Again!
          </v-btn>
        </v-col>
        <v-col md="2" cols="6">
          <v-select
              v-model="numRandomWords"
              label="Num random"
              :items="[5,10,15,20,30,50]"
              variant="underlined"
          ></v-select>
        </v-col>
        <v-col cols="6" md="">
          <v-select
              multiple
              clearable
              v-model="randomFilterByTags"
              label="Filter vocab by tags"
              :items="tagsSorted"
              variant="underlined"
          ></v-select>
        </v-col>
        <v-col cols="6" md="">
          <v-select
              multiple
              clearable
              v-model="grammarFilterByLesson"
              label="Filter grammar"
              :items="grammarLessonSetSorted"
              variant="underlined"
          ></v-select>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <h1>Word search:</h1>
          <v-text-field label="Seach" variant="outlined" v-model="searchTerm" @click:append="onSearchTermChange" append-icon="message"></v-text-field>
        </v-col>
      </v-row>
      <div v-for="(note, i) in searchResults" :key="'note'+i" class="search-results himalaya">
        <SearchResult :note="note" :styleTibetan="styleTibetan" idx="i" :basePath="basePath"/>
      </div>
      <v-row class="vertical-spacer"></v-row>
      <v-row class="header-row">
        <v-col>
          <h1>Time and Person</h1>
        </v-col>
        <v-col cols="auto">
          <v-btn @click="random_personAndTimeForDrilling" rounded="xl" size="small">
            R!
          </v-btn>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="himalaya">
          <p v-html="styleTibetan(personAndTimeForDrilling.past)"></p>
          <p v-html="styleTibetan(personAndTimeForDrilling.present)"></p>
          <p v-html="styleTibetan(personAndTimeForDrilling.future)"></p>
        </v-col>
        <v-col>
          <p v-html="styleTibetan(personAndTimeForDrilling.firstPerson)"></p>
          <p v-html="styleTibetan(personAndTimeForDrilling.secondPerson)"></p>
          <p v-html="styleTibetan(personAndTimeForDrilling.thirdPerson)"></p>
        </v-col>
      </v-row>
      <v-row class="vertical-spacer"></v-row>
      <v-row class="header-row">
        <v-col>
          <h1>Random Vocab</h1>
        </v-col>
        <v-col cols="auto">
          <v-btn @click="random_notes" rounded="xl" size="small">
            R!
          </v-btn>
        </v-col>
      </v-row>
      <div v-for="(note, i) in randomNotes" :key="note.nid" class="search-results">
        <SearchResult :note="note" :styleTibetan="styleTibetan" idx="i" isRandomNotes="true" :id="'note-'+note.nid" :basePath="basePath"/>
      </div>
      <v-row class="vertical-spacer"></v-row>
      <v-row class="header-row">
        <v-col>
          <h1>Random Grammar Points</h1>
        </v-col>
        <v-col cols="auto">
          <v-btn @click="random_grammarCard" rounded="xl" size="small">
            R!
          </v-btn>
        </v-col>
      </v-row>
      <v-row class="grammar-card-row" v-for="(card, i) in randomGrammarCards" :key="'card'+i" align="start" justify="start" style="margin-bottom: 10px">
        <v-col v-if="card.Example" v>
          <div class="grammar-card-card" v-html="styleTibetan(card.Example)"></div>
        </v-col>
        <v-col>
          <div class="grammar-card-card" v-html="styleTibetan(card.Card)"></div>
        </v-col>
        <v-col cols="12" style="border-top: 1px solid rgba(211,211,211,0.25)">
          <v-row align="end">
            <v-col cols="9">
              <div class="grammar-card-hint" v-html="styleTibetanSmaller(`${card.Hint}`)"></div>
            </v-col>
            <v-col cols="3" style="text-align: right; font-size: 80%; color: lightgray;" v-if="card.Lesson">
              <v-btn variant="outlined" size="small" class="grammar-card-hint" v-html="styleTibetanSmaller(`${card.Lesson}`)" @click="showLessonPdf(card)"></v-btn>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
      <v-row class="vertical-spacer"></v-row>
      <v-row class="header-row">
        <v-col>
          <h1>Drilling Permutations</h1>
        </v-col>
        <v-col cols="auto">
          <v-btn @click="random_allPermutations" rounded="xl" size="small">
            R!
          </v-btn>
        </v-col>
      </v-row>
      <div v-if="width > 600">
        <v-row class="permutations-row" v-for="(p, i) in allPermutations" :key="'p'+i" align="center" justify="start">
          <v-col cols="4" sm="2">
            <div class="permutations-tense">{{ p.tense }}</div>
          </v-col>
          <v-col cols="8" sm="5">
            <div class="permutations-tenseText" v-html="styleTibetan(p.tenseText)"></div>
          </v-col>
          <v-col cols="6" sm="auto">
            <div class="permutations-posNeg">{{ p.posNeg }}</div>
          </v-col>
          <v-col cols="6" sm="auto">
            <div class="permutations-questionStatement">{{ p.questionStatement }}</div>
          </v-col>
        </v-row>
      </div>
      <v-row v-else class="permutations-row" v-for="(p, i) in allPermutations" :key="'p'+i" align="center" justify="start">
        <v-col cols="12">
          <span class="permutations-tenseText" v-html="styleTibetan(p.tenseText)+' '"></span>
          <span class="permutations-posNeg">{{ p.posNeg + " "}}</span><span class="permutations-questionStatement">{{ p.questionStatement }}</span>
        </v-col>
      </v-row>
    </v-container>
  </main>
</template>

<style>
.tibetan {
  font-size:180%;
  line-height: 170%;
}
.tibetan-smaller {
  font-size:130%;
  line-height: 160%;
}
</style>

<style scoped>

@media only screen and (max-width: 600px) {
  main {
    font-size: 14px;
  }
  h1 {
    font-size: 18px;
  }
}

.vertical-spacer {
  height: 40px;
}

.noteback {
  line-height: 40px;
  vertical-align: center;
}

.grammar-card-row:nth-child(odd), .random-notes-row:nth-child(odd), .permutations-row:nth-child(odd),.search-results:nth-child(odd) {
  background-color: #fffce9;
}

.grammar-card-card {
}
.grammar-card-hint {
  color: #2c3e50;
}

.permutations-row {
}

.permutations-tenseText {
}

.header-row {
  margin-bottom: 20px;
  border-bottom: solid 1px black;
}

</style>
