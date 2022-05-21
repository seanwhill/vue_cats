<template>
<div class="animals flex flex-wrap -mx-5">
  <AnimalCard
    v-for="animal in animals"
    :key="animal.breed"
    :animal="animal"
    class="mb-10 mr-10"/>
</div>

</template>

<script>
export default {
  props: {
    animals: {
      type: Array,
      default: () => []
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
