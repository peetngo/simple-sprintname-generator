<template>
  <div id="app" class="container">
  <header>
    <span>Sprint Name Generator</span>
  </header>
  <main>
    <b-field label="Required">
      <b-select placeholder="Select Sprint Letter" required v-model="option">
        <option value="A">A</option>
        <option value="B">B</option>
        <option value="C">C</option>
        <option value="D">D</option>
        <option value="E">E</option>
        <option value="F">F</option>
        <option value="G">G</option>
        <option value="H">H</option>
        <option value="I">I</option>
        <option value="J">J</option>
        <option value="K">K</option>
        <option value="L">L</option>
        <option value="M">M</option>
        <option value="N">N</option>
        <option value="O">O</option>
        <option value="P">P</option>
        <option value="Q">Q</option>
        <option value="R">R</option>
        <option value="S">S</option>
        <option value="T">T</option>
        <option value="U">U</option>
        <option value="V">V</option>
        <option value="W">W</option>
        <option value="X">X</option>
        <option value="Y">Y</option>
        <option value="Z">Z</option>
      </b-select>
    </b-field>
    <b-field label="" required>
      <b-input v-model="key"  placeholder="Input similar word, ex: Happy"></b-input>
    </b-field>
    <div>
      <b-button type="is-primary" v-on:click="getWord(option, key)">Get word!</b-button>
    </div>
    <div class="words" v-for="word in words" v-bind:key="word.word">
     <p> {{word.word}} </p>
    </div>

  </main>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: 'app',
  data() {
    return {
    words: []
    }
  },
    methods: {
      getWord(letter, description) {

          if (letter || description) {
              axios.get('https://api.datamuse.com/words?ml=' + description + '&sp=' + letter + '*' +'&max=100')
                      .then(response =>
                      {
                        this.words = response.data
                      })
          }
      }
    }
}
</script>

<style>


</style>
