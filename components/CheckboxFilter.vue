<template>
  <div class="relative inline-block text-left">
    <div>
      <button
      type="button"
      @click="openCloseFilter"
      class="inline-flex justify-center w-full rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-sm font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-indigo-500"
      id="menu-button"
      aria-expanded="true"
      aria-haspopup="true">
        {{filterData.label}}
        <!-- Heroicon name: solid/chevron-down -->
        <svg class="-mr-1 ml-2 h-5 w-5" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
          <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" />
        </svg>
      </button>
    </div>

  <!--
    Dropdown menu, show/hide based on menu state.

    Entering: "transition ease-out duration-100"
      From: "transform opacity-0 scale-95"
      To: "transform opacity-100 scale-100"
    Leaving: "transition ease-in duration-75"
      From: "transform opacity-100 scale-100"
      To: "transform opacity-0 scale-95"
  -->
    <div
    v-if="this.menuOpened"
    class="menu origin-top-right absolute right-0 mt-2rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 divide-y divide-gray-100 focus:outline-none"
    role="menu"
    aria-orientation="vertical"
    aria-labelledby="menu-button"
    tabindex="-1">
      <ul role="list" class="font-medium text-gray-900 px-2 py-3">
        <li :key="menuItem.name" v-for="menuItem in filterData.menuItems">
          <input type="checkbox" :id="menuItem.name" :name="menuItem.name" :checked="menuItem.checked" @click="checkMenuItem(menuItem.id)">
          <label :for="menuItem.name">{{menuItem.name}}</label>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
export default {
  data () {
    return {
      menuOpened: false
    }
  },
  props: {
    filterData: Object
  },
  methods: {
    checkMenuItem (id) {
      this.$emit('check-menu', id)
    },
    openCloseFilter () {
      this.menuOpened = !this.menuOpened
    }

  }
}
</script>

<style scoped>
  .menu {
    z-index: 1000;
    width: 100%;
  }
</style>
