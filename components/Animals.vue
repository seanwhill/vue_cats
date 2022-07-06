<template>
<div class="animals flex flex-wrap -mx-5">
  <AnimalCard
    v-for="animal in displayedAnimals"
    :key="animal.id"
    :animal="animal"
    @like-animal="$emit('like-animal', animal.id)"
    class="mb-10 mr-10"/>
</div>

</template>

<script>
export default {
  props: {
    animals: Array,
    selectedBreeds: Set,
    selectedCategories: Set
  },
  computed: {
    displayedAnimals () {
      return this.animals.filter((animal) => {
        // TODO SHOULD USE GUARD IF STATEMENTS
        // let display = true

        // if (this.selectedCategories.size !== 0 && !this.selectedCategories.has(animal.category)) {
        //   display = false
        // }
        // if (this.selectedBreeds.size !== 0 && !this.selectedBreeds.has(animal.breed)) {
        //   display = false
        // }

        // TODO used twice. Move to helper function
        let display = false

        if (this.selectedBreeds.size === 0 && this.selectedCategories.size === 0) {
          display = true
        } else if (this.selectedBreeds.size === 0 && this.selectedCategories.has(animal.category)) {
          display = true
        } else if (this.selectedCategories.size === 0 && this.selectedBreeds.has(animal.breed)) {
          display = true
        } else if (this.selectedBreeds.has(animal.breed) && this.selectedCategories.has(animal.category)) {
          display = true
        }
        return display
      })
    }
  }
}
</script>

<style>
.animals {
  display: flex;
  flex-direction: row;
  text-align: center;
  justify-content: center;
}

</style>
