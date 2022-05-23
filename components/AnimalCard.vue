<template>
  <div class="max-w-xs rounded overflow-hidden shadow-lg animal flex flex-col">
    <div>
      <div class="img-overlay-wrap">
        <img class="w-full" :src="animal.image" :alt="animal.image">

        <svg
        @click="onLiked(animal.id)"
        xmlns="http://www.w3.org/2000/svg"
        class="h-6 w-6 heart"
        :fill="animal.liked ? '#fd45c9' : 'none'"
        viewBox="0 0 24 24"
        stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
        </svg>
      </div>
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
  },
  data () {
    return {
      liked: false
    }
  },
  methods: {
    onLiked (id) {
      this.$emit('like-animal', id)
      // this.likeAnimal(id)
    }
  }
}
</script>
<style scoped>
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

.heart {
  stroke-width: 2;
  stroke: #fd45c9;
  width: 50px;
  height: 50px;
}

.img-overlay-wrap {
  position: relative;
  display: inline-block; /* <= shrinks container to image size */
  transition: transform 150ms ease-in-out;
}

.img-overlay-wrap img { /* <= optional, for responsiveness */
  display: block;
  max-width: 100%;
  height: auto;
}

.img-overlay-wrap svg {
  position: absolute;
  top: 10%;
  left: 77%;
}

</style>
