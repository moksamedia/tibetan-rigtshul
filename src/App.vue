<script setup>

const firstPerson = [
  'ང་',
  'ང་ཚོ་',
  'རང་',
  'ང་རང་',
  'ང་གཉིས་',
  'ང་དང་རོགས་པ་དེ་མཉམ་དུ་',
  'ང་ཚོ་ཚང་མ་'
]

const secondPerson = [
  'ཁྱེད་རང་',
  'ཁྱེད་རང་ཚོ་',
  'ཁྱོད་',
  'ཁྱོད་རྣམ་',
  'ཁྱེད་རང་ཚོ་ཚང་མ་',
  'ཁྱེད་རང་གཉིས་',
  'ཁྱེད་རང་གསུམ་'
]

const thirdPerson = [
  'ཁོང་',
  'མོ་ལགས་',
  'ཁོ་',
  'ལྷ་མོ་',
  'ཁོང་གི་གྲོགས་པོ་',
  'སློབ་ཕྲུག་དེ་',
  'རྨོ་རྨོ་ལགས་',
  'ང་ཇོ་ཇོ་ལགས་',
  'རྒན་ལགས་',
  'རིན་པོ་ཆེ་དེ་ཚོ་ལགས་',
  'རྫ་མཁན་རྣམས་',
  'ཨ་ཅག་ལགས་',
  'སྒྲོལ་མ་',
  'ངའི་ཨ་ཁུ་',
  'ཁྱེད་རང་ཀྱི་ཨ་མ་ལགས་',
  'རྒྱ་གར་ཚོ་',
]

const past = [
  'སྔོན་མ་',
  'ཁ་སང་',
  'དེ་རིང་སྔོན་མ་',
  'བདུན་ཕྲག་སྔོན་མ་ལ་',
  'དེ་རིང་ཞིགས་པ་',
  'གཟའ་འཁོར་སྔོན་མ་ལ་',
  'བདང་དགོང་',
  'ཆུང་དུས་',
  'ཁ་ས་དགོང་དག་',
  'ཁ་སིང་',
  'ལོ་སྔོན་མར་',
  'གཟའ་པ་སངས་སྔོན་མ་ལ་',
  'ལོ་ཁ་ཤེས་སྔོན་ལ་'
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
  'མ་ཨོངས་པར་',
  'དེ་དགོང་',
  'གནངས་ཉིན་ཀ་',
  'གནངས་ཉིན་',
  'གཞེས་ཉིན་',
  'ཉིན་མ་གཅིག་',
  'གཟའ་ཟླ་བ་རྗེས་མ་ལ་',
  'གཟའ་པ་སངས་རྗེས་མ་ལ་',
  'དགུན་ཁ་རྗེས་མ་སྐབས་ལ་',
  'གཟའ་མཇུག་རྗེས་མར་'
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
    </v-container>
  </main>
</template>

<style scoped>

.tibetan {
  font-size: 40px;
}

</style>
