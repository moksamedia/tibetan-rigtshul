<script setup>
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
let randomNotes = sampleSize(notes, 20)

function compareNotes(a,b) {
  return a.part_of_speech < b.part_of_speech
}

randomNotes = randomNotes.sort(compareNotes)

let randomGrammarCards = sampleSize(grammarCards, 20)

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
  'ང་ཇོ་ཇོ་ལགས་',
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
	'བོད་ཡིག་དགེ་རྒན་'
]

const past = [
  'སྔོན་མ་',
  'ཁ་སང་',
  'དེ་རིང་སྔོན་མ་',
  'བདུན་ཕྲག་སྔོན་མ་',
  'དེ་རིང་ཞོགས་པ་',
  'གཟའ་འཁོར་སྔོན་མ་ལ་',
  'བདང་དགོང་',
  'ཆུང་དུས་',
  'ཁ་ས་དགོང་དག་',
  'ཁ་སིང་',
  'ལོ་སྔོན་མར་',
  'གཟའ་པ་སངས་སྔོན་མ་ལ་',
  'ལོ་ཁ་ཤེས་སྔོན་ལ་',
	'གཟའ་མཇུག་སྔོན་མར་',
	'ལོ་ཁ་ཤས་ཀྱི་སྔོན་ལ་'
]

const present = [
  'ད་ལྟ་',
  'དེང་སང་',
  'ཉེ་ཆར་',
  'ཉིན་ལྟར་',
  'ཉི་མ་ཉིན་གང་',
  'ལོ་ལྟར་རེད་བཞིན་',
  'ད་ལྟ་ལམ་སང་',
  'ད་ལྟ་རང་',
  'ད་རེས་',
]

const future = [
  'སང་ཉིན་',
  'མ་འོངས་པར་',
  'དེ་དགོང་',
  'གནངས་ཉིན་ཀ་',
  'གནངས་ཉིན་',
  'གཞེས་ཉིན་',
  'ཉིན་མ་གཅིག་',
  'གཟའ་ཟླ་བ་རྗེས་མ་ལ་',
  'གཟའ་པ་སངས་རྗེས་མ་ལ་',
  'དགུན་ཁ་རྗེས་མ་སྐབས་ལ་',
  'གཟའ་མཇུག་རྗེས་མར་',
	'རྗེས་ལ་',
	'དུས་ཚོད་སྟོང་པ་རག་ན་',
	'གུང་སེང་གི་སྐབས་ལ་'
]

function rand(array) { return array[Math.floor(Math.random() * array.length)] };

</script>

<template>
  <main>
    <v-container>
      <v-row>
        <v-col>
          <p class="tibetan">{{rand(past)}}</p>
        </v-col>
        <v-col>
          <p class="tibetan">{{rand(firstPerson)}}</p>
          <p class="tibetan">{{rand(secondPerson)}}</p>
          <p class="tibetan">{{rand(thirdPerson)}}</p>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <p class="tibetan">{{rand(present)}}</p>
        </v-col>
        <v-col>
          <p class="tibetan">{{rand(firstPerson)}}</p>
          <p class="tibetan">{{rand(secondPerson)}}</p>
          <p class="tibetan">{{rand(thirdPerson)}}</p>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <p class="tibetan">{{rand(future)}}</p>
        </v-col>
        <v-col>
          <p class="tibetan">{{rand(firstPerson)}}</p>
          <p class="tibetan">{{rand(secondPerson)}}</p>
          <p class="tibetan">{{rand(thirdPerson)}}</p>
        </v-col>
      </v-row>
      <v-row style="height:100px;"></v-row>
      <v-row class="random-notes-row" v-for="note in randomNotes" align="center" justify="center" no-gutters>
        <v-col>
          <span class="tibetan2">{{ note.front }}</span>
        </v-col>
        <v-col>
          <span class="noteback">({{note.part_of_speech}}) {{note.back}}</span>
        </v-col>
      </v-row>
      <v-row style="height:100px;"></v-row>
      <v-row class="grammar-card-row" v-for="card in randomGrammarCards" align="start" justify="start">
        <v-col>
          <div class="grammar-card-card align-start">{{ card.Card }}</div>
        </v-col>
        <v-col>
          <div class="grammar-card-hint align-start">{{card.Hint}} {{card.Lesson}}</div>
        </v-col>
      </v-row>
    </v-container>
  </main>
</template>

<style scoped>

.tibetan {
  font-size: 30px;
}

.tibetan2 {
  font-size: 30px;
}

.noteback {
  line-height: 40px;
  vertical-align: center;
}

.grammar-card-row:nth-child(odd), .random-notes-row:nth-child(odd) {
  background-color: beige;
}

.grammar-card-card {
  font-size: 20px;
}
.grammar-card-hint {
  font-size: 20px;
  color: #2c3e50;
}

</style>
