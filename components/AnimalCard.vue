<template>
  <div class="max-w-xs rounded overflow-hidden shadow-lg animal flex flex-col">
    <div>
      <img class="w-full" :src="animal.image" :alt="animal.image">
      <div class="px-6 py-4">
      <div class="font-bold text-xl mb-2">{{animal.breed}}</div>
        <p class="text-gray-500 text-base">
          {{animal.description}}
        </p>
      </div>
    </div>
    <div class="mt-auto mb-5 ml-5">
      <button class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded float-left ">
        More Info
      </button>
    </div>

  </div>
</template>

<script>
export default {
  props: {
    animal: {
      type: Object,
      default: () => {}
    }
  }
}
</script>
<style>
img {
  /* float: left;
  height: 400px; */
  object-fit: cover;
  max-width: 100%;
  max-height: 100%;
  vertical-align: middle;
}

.animal {
  float: none;
}
</style>
