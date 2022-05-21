<template>
  <div class="flex-container">
      <Animals :animals="animals"/>
  </div>
</template>

<script setup>

export default {
  async fetch () {
    let res = await fetch('https://vue-mock-api.openlypreview.com/api/cats')
    res = await res.json()

    // TODO: Can potentially modify the width or height if a certain standard is desired.
    res.forEach((animal) => {
      const sizeRegex = /&w=\d*/i
      animal.image = animal.image.replace(sizeRegex, '&w=400&h=400')
      console.log(animal.image)
    })

    this.animals = res
  },
  data () {
    return {
      animals: []
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
