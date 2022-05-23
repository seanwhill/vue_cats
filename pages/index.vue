<template>
  <div>
    <Header :likes="countLikes"/>
    <div class="mb-9 ml-10">
      <CheckboxFilter :filterData="breedFilter" @check-menu="checkBreedMenuItem" class="mr-5"/>
      <CheckboxFilter :filterData="categoryFilter" @check-menu="checkCategoryMenuItem"/>
    </div>
    <div class="flex-container">
        <Animals :animals="animals" @like-animal="likeAnimal"/>
    </div>
  </div>
</template>

<script setup>

export default {
  async fetch () {
    let res = await fetch('https://vue-mock-api.openlypreview.com/api/cats')
    res = await res.json()

    // set to know which breeds we added already
    const breeds = new Set()
    // set to know which breeds are selected

    const breedFilter = {
      label: 'Filter By Breed',
      menuItems: []
    }

    // set to know which categories we added already
    const categories = new Set()
    // set to know which categories are selected

    const categoryFilter = {
      label: 'Filter By Category',
      menuItems: []
    }

    let animalId = 0
    let breedId = 0
    let categoryId = 0
    res.forEach((animal) => {
      // TODO: Can potentially modify the width or height if a certain standard is desired.
      const sizeRegex = /&w=\d*/i
      animal.image = animal.image.replace(sizeRegex, '&w=400&h=400')
      console.log(animal.image)

      // animals default liked and displayed
      animal.id = animalId++
      animal.liked = false
      animal.display = true

      // build breed filter menu items
      if (!breeds.has(animal.breed)) {
        breeds.add(animal.breed)
        breedFilter.menuItems.push({ name: animal.breed, checked: false, id: breedId++ })
      }

      // build category filter menu items
      if (!categories.has(animal.category)) {
        categories.add(animal.category)
        categoryFilter.menuItems.push({ name: animal.category, checked: false, id: categoryId++ })
      }
    })

    this.breedFilter = breedFilter
    this.categoryFilter = categoryFilter
    this.animals = res
  },
  data () {
    return {
      animals: Array,
      likes: Number,
      breedFilter: Object,
      categoryFilter: Object,
      selectedBreeds: new Set(),
      selectedCategories: new Set()
    }
  },
  methods: {
    likeAnimal (id) {
      this.animals = this.animals.map((animal) => {
        if (animal.id === id) {
          animal.liked = !animal.liked
        }
        return animal
      })
      // this.$set(animals, id, )
    },
    checkBreedMenuItem (id) { // TODO REFACTOR
      const breed = this.breedFilter.menuItems[id].name

      const checkValue = !this.breedFilter.menuItems[id].checked
      this.breedFilter.menuItems[id].checked = checkValue

      console.log(!checkValue && this.selectedCategories.size === 0 && this.selectedBreeds.size === 1)
      this.animals = this.animals.map((animal) => {
        if (!checkValue && this.selectedCategories.size === 0 && this.selectedBreeds.size === 1) {
          animal.display = true
        } else if (!checkValue && this.selectedBreeds.size === 1) {
          if (this.selectedCategories.has(animal.category)) {
            animal.display = true
          }
        } else if (breed === animal.breed) {
          if (checkValue) {
            if (this.selectedCategories.size === 0 || this.selectedCategories.has(animal.category)) {
              animal.display = true
            } else {
              animal.display = false
            }
          } else if (!checkValue) {
            animal.display = false
          }
        } else if (!this.selectedBreeds.has(animal.breed)) {
          animal.display = false
        }

        return animal
      })
      checkValue ? this.selectedBreeds.add(breed) : this.selectedBreeds.delete(breed)
    },
    checkCategoryMenuItem (id) { // TODO REFACTOR
      const category = this.categoryFilter.menuItems[id].name

      const checkValue = !this.categoryFilter.menuItems[id].checked
      this.categoryFilter.menuItems[id].checked = checkValue

      this.animals = this.animals.map((animal) => {
        if (!checkValue && this.selectedBreeds.size === 0 && this.selectedCategories.size === 1) {
          animal.display = true
        } else if (!checkValue && this.selectedCategories.size === 1) {
          if (this.selectedBreeds.has(animal.breed)) {
            animal.display = true
          }
        } else if (category === animal.category) {
          if (checkValue) {
            if (this.selectedBreeds.size === 0 || this.selectedBreeds.has(animal.breed)) {
              animal.display = true
            } else {
              animal.display = false
            }
          } else if (!checkValue) {
            animal.display = false
          }
        } else if (!this.selectedCategories.has(animal.category)) {
          animal.display = false
        }

        return animal
      })
      checkValue ? this.selectedCategories.add(category) : this.selectedCategories.delete(category)
    },
    isEmptyFilterSelection () {
      return this.selectedBreeds.size === 0 && this.selectedCategories.size === 0
    }
  },
  computed: {
    countLikes () {
      let likes = 0
      this.animals.forEach((animal) => {
        if (animal.liked && animal.display) {
          likes++
        }
      })
      return likes
    }
  }

}

</script>

<style>
.flex-container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
