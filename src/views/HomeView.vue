<template>
  <div class="home">
    <header class="my-5 mx-1">
      <h1
        class="font-Nunito font-semibold text-6xl tracking-wider text-white uppercase pb-3 border-b border-white"
      >
        explore the universe
      </h1>
      <img
        src="../assets/images/coverCarina.webp"
        alt="Nebula Carina JWST"
        class="w-full mt-2"
      />
    </header>
    <form @submit.prevent="SearchImages()" class="flex flex-col items-center">
      <input
        class="border border-white rounded w-1/2 sm:w-48 outline-none text-white pl-1"
        type="text"
        placeholder="e.g. moon"
        v-model="search"
      />
      <input
        type="submit"
        value="Search"
        class="border border-white px-2 rounded mt-2 text-center uppercase font-light text-white"
      />
    </form>
    <div class="flex flex-col justify-center items-center">
      <CardComponent :nasaImages="nasaImages" />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import { ref } from 'vue';
import CardComponent from '../components/CardComponent.vue';

export default {
  name: 'HomeView',
  components: { CardComponent },
  setup() {
    const search = ref('');
    const nasaImages = ref([]);

    const SearchImages = () => {
      if (search.value != '') {
        fetch(`https://images-api.nasa.gov/search?q=${search.value}`)
          .then((response) => response.json())
          .then((data) => {
            nasaImages.value = data.collection.items.slice(0, 9);
            search.value = '';
            console.log(nasaImages.value);
          });
      }
    };
    return {
      search,
      nasaImages,
      SearchImages,
    };
  },
};
</script>
