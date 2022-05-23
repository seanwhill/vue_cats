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
    likeAnimal: Function
  },
  computed: {
    displayedAnimals () {
      return this.animals.filter((animal) => {
        console.log(animal)
        return animal.display
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
