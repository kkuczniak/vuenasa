<template>
  <div class="home mt-5">
    <div class="imageCard">
      <router-link to="">hello</router-link>
    </div>
    <form @submit.prevent="SearchImages()" class="flex flex-col items-center">
      <input
        class="border border-black rounded w-1/2 md:w-44 outline-none"
        type="text"
        placeholder="e.g. Saturn"
        v-model="search"
      />
      <input
        type="submit"
        value="Search"
        class="border border-black rounded mt-2 text-center uppercase"
      />
    </form>
    <CardComponent :nasaImages="nasaImages" />
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
