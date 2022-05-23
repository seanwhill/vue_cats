<template>
<div class="animals flex flex-wrap -mx-5">
  <AnimalCard
    v-for="animal in displayedAnimals"
    :key="animal.id"
    :animal="animal"
    :likeAnimal="likeAnimal"
    @like-animal="$emit('like-animal', animal.id)"
    class="mb-10 mr-10"/>
</div>

</template>

<script>
export default {
  props: {
    animals: Array,
    likeAnimal: Function,
    selectedBreeds: Set,
    selectedCategories: Set
  },
  computed: {
    displayedAnimals () {
      return this.animals.filter((animal) => {
        let display = false

        // TODO used twice. Move to helper file
        if (this.selectedBreeds.size === 0 && this.selectedCategories.size === 0) {
          display = true
        } else if (this.selectedBreeds.size === 0 && this.selectedCategories.size !== 0 && this.selectedCategories.has(animal.category)) {
          display = true
        } else if (this.selectedBreeds.size !== 0 && this.selectedCategories.size === 0 && this.selectedBreeds.has(animal.breed)) {
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
