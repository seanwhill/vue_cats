<template>
  <div>
    <Header :likes="countLikes"/>
    <div class="mb-9 ml-10">
      <CheckboxFilter :filterData="breedFilter" @check-menu="checkBreedMenuItem" class="mr-5"/>
      <CheckboxFilter :filterData="categoryFilter" @check-menu="checkCategoryMenuItem"/>
    </div>
    <div class="flex-container">
        <Animals :animals="animals" @like-animal="likeAnimal" :selectedBreeds="selectedBreeds" :selectedCategories="selectedCategories"/>
    </div>
  </div>
</template>
