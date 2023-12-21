<script>
import notes from './assets/notes.csv'
import grammarCards from './assets/grammar-cards.csv'

const sampleSize = ([...arr], n = 1) => {
  let m = arr.length;
  while (m) {
    const i = Math.floor(Math.random() * m--);
    [arr[m], arr[i]] = [arr[i], arr[m]];
  }
  return arr.slice(0, n);
};

function compareNotes(a,b) {
  return a.part_of_speech < b.part_of_speech
}

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
import {ref, onMounted} from 'vue'
import { useDisplay } from 'vuetify'
const { width, mobile } = useDisplay()

let searchTerm = ref('')
let searchResults = ref([])
let randomNotes = ref([])
let randomGrammarCards = ref([])
let permutations = ref([])
let allPermutations = ref([])
let timeAndPersonPermutations = ref([])
let personAndTimeForDrilling = ref({})

function onSearchTermChange() {
  if (searchTerm.value == null || searchTerm.value.trim() === "") {
    searchResults.value = [];
  }
  else {
    searchResults.value = notes.filter(note => note.front.includes(searchTerm.value) || note.back.includes(searchTerm.value))
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
  timeAndPersonPermutations.value =  [
    {tense:'PAST', tenseText: `${rand(past)} ${rand(firstPerson)}`},
    {tense:'PAST', tenseText: `${rand(past)} ${rand(secondPerson)}`},
    {tense:'PAST', tenseText: `${rand(past)} ${rand(thirdPerson)}`},
    {tense:'PRESENT', tenseText: `${rand(present)} ${rand(firstPerson)}`},
    {tense:'PRESENT', tenseText: `${rand(present)} ${rand(secondPerson)}`},
    {tense:'PRESENT', tenseText: `${rand(present)} ${rand(thirdPerson)}`},
    {tense:'FUTURE', tenseText: `${rand(future)} ${rand(firstPerson)}`},
    {tense:'FUTURE', tenseText: `${rand(future)} ${rand(secondPerson)}`},
    {tense:'FUTURE', tenseText: `${rand(future)} ${rand(thirdPerson)}`},
  ]
}

function random_notes() {
  randomNotes.value = sampleSize(notes, 20).sort(compareNotes)
}

function random_grammarCard() {
  randomGrammarCards.value = sampleSize(grammarCards, 20)
}

function random_allPermutations() {
  random_timeAndPersonPermutations()
  permutations.value = questionStatement.flatMap(a => posNeg.map(c => {return {questionStatement:a, 'posNeg': c}}))
  allPermutations.value = timeAndPersonPermutations.value.flatMap(d => permutations.value.map(v => {return {...v,...d}}))
}

function randomize() {
  random_personAndTimeForDrilling()
  random_notes()
  random_grammarCard()
  random_timeAndPersonPermutations()
  random_allPermutations()
}

onMounted(() => {
  randomize(),
      mobile
})

</script>

<template>
  <main>
    <v-container>
      <v-row>
        <v-col>
          <v-btn @click="randomize">
            Randomize Again!
          </v-btn>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <h1>Word search:</h1>
          <v-text-field label="Seach" variant="outlined" v-model="searchTerm" @input="onSearchTermChange"></v-text-field>
        </v-col>
      </v-row>
      <v-row class="search-results" v-for="(note, i) in searchResults" :key="'note'+i" align="center" justify="start">
        <v-col cols="auto">
          <div class="search-results-front">{{ note.front }}</div>
        </v-col>
        <v-col>
          <div class="search-results-back">{{note.back}}</div>
        </v-col>
      </v-row>
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
        <v-col>
          <p class="tibetan">{{personAndTimeForDrilling.past}}</p>
          <p class="tibetan">{{personAndTimeForDrilling.present}}</p>
          <p class="tibetan">{{personAndTimeForDrilling.future}}</p>
        </v-col>
        <v-col>
          <p class="tibetan">{{personAndTimeForDrilling.firstPerson}}</p>
          <p class="tibetan">{{personAndTimeForDrilling.secondPerson}}</p>
          <p class="tibetan">{{personAndTimeForDrilling.thirdPerson}}</p>
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
      <v-row class="random-notes-row" v-for="(note,i) in randomNotes" :key="'note'+i" align="center" justify="center" no-gutters>
        <v-col>
          <span class="tibetan2">{{ note.front }}</span>
        </v-col>
        <v-col>
          <span class="noteback">({{note.part_of_speech}}) {{note.back}}</span>
        </v-col>
      </v-row>
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
      <v-row class="grammar-card-row" v-for="(card, i) in randomGrammarCards" :key="'card'+i" align="start" justify="start">
        <v-col>
          <div class="grammar-card-card align-start">{{ card.Card }}</div>
        </v-col>
        <v-col>
          <div class="grammar-card-hint align-start">{{card.Hint}} {{card.Lesson}}</div>
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
      <v-row v-if="!mobile" class="permutations-row" v-for="(p, i) in allPermutations" :key="'p'+i" align="center" justify="start">
        <v-col cols="4" sm="2">
          <div class="permutations-tense">{{ p.tense }}</div>
        </v-col>
        <v-col cols="8" sm="5">
          <div class="permutations-tenseText">{{ p.tenseText }}</div>
        </v-col>
        <v-col cols="6" sm="auto">
          <div class="permutations-posNeg">{{ p.posNeg }}</div>
        </v-col>
        <v-col cols="6" sm="auto">
          <div class="permutations-questionStatement">{{ p.questionStatement }}</div>
        </v-col>
      </v-row>
      <v-row v-else class="permutations-row" v-for="(p, i) in allPermutations" :key="'p'+i" align="center" justify="start">
        <v-col cols="12">
          <span class="permutations-tenseText">{{ p.tenseText + " "}}</span>
          <span class="permutations-posNeg">{{ p.posNeg + " "}}</span><span class="permutations-questionStatement">{{ p.questionStatement }}</span>
        </v-col>
      </v-row>
    </v-container>
  </main>
</template>

<style scoped>

.vertical-spacer {
  height: 40px;
}

h4.tibetan {
  text-decoration: underline;
}

.tibetan, .search-results-front {
  font-size: 30px;
}

.tibetan2 {
  font-size: 30px;
}

.noteback {
  line-height: 40px;
  vertical-align: center;
}

.grammar-card-row:nth-child(odd), .random-notes-row:nth-child(odd), .permutations-row:nth-child(odd),.search-results:nth-child(odd) {
  background-color: #fffce9;
}

.grammar-card-card {
  font-size: 20px;
}
.grammar-card-hint {
  font-size: 20px;
  color: #2c3e50;
}

.permutations-row {
  font-size: 18px;
}

.permutations-tenseText {
  font-size: 30px;
}

.header-row {
  margin-bottom: 20px;
  border-bottom: solid 1px black;
}
</style>
