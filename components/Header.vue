<template>

  <nav class="navbar navbar-expand-lg shadow-md py-2 bg-white relative flex items-center w-full justify-between mb-9">
    <div class="px-6 w-full flex flex-wrap items-center justify-between">
      <h1 class="font-medium leading-tight text-5xl mt-0 ml-8">Cats!</h1>
      <div class="favorites">
        <h2 class="font-medium leading-tight text-3xl mt-0 ml-20 float-left">Favorites</h2>
        <div class="favorites-heart">
          <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6 heart"
          fill="#fd45c9"
          viewBox="0 0 24 24"
          stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
          </svg>
          <p class="likes">{{likes}}</p>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
export default {
  props: {
    likes: Number
  }
}
</script>
<style scoped>
  .favorites {
    align-items: center;
    display: flex;
  }

  .heart {
    stroke-width: 2;
    stroke: #fd45c9;
    width: 50px;
    height: 50px;
  }

  .favorites-heart {
    position: relative;
    text-align: center;
    color: white;
  }

  .likes {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

</style>
