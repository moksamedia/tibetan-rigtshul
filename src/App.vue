<script setup>

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
  'མཐའ་མ་ལ་',
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

function rand(array) { return array[Math.floor(Math.random() * array.length)] };

</script>

<template>
  <main>
    <v-container>
      <v-row>
        <v-col>
          <p>positive // negative // direct // inferential, habitual</p>
          <p>question // present perfect</p>
        </v-col>
      </v-row>
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
    </v-container>
  </main>
</template>

<style scoped>

h4.tibetan {
  text-decoration: underline;
}

.tibetan {
  font-size: 30px;
}

</style>
