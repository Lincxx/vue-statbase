<template>
  <div @click="switchCharacter" class="col-md-4">
    <div class="character-card">
      <div class="card-block">
        <h4 class="card-title"> {{character.name}}</h4>
        <div class="card-text">Height:  {{character.height}} cm</div>
        <div class="card-text">Mass:  {{character.mass}} kg</div>
        <div class="card-text">Hair Color:  {{character.hair_color}}</div>
        <div class="card-text">Eye Color:  {{character.eye_color}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'character',
  props: ['id'],
  data() {
    return {
      character: {}
    }
  },
  methods: {
     fetchCharacter(id) {
      fetch(`https://swapi.co/api/people/${id}`, {
        method: 'GET'
      })
      .then(response => response.json())
      .then(json => this.character = json)
    },
    switchCharacter(){
      let random_id = Math.floor(Math.random() * 83) + 1
      this.fetchCharacter(random_id)
    }
  },
  created() {
    this.fetchCharacter(this.id)
  }
}
</script>

<style>

</style>

