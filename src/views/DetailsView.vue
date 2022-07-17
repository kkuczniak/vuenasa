<template>
  <div class="details text-white flex flex-col items-center">
    <h1 class="font-semibold text-2xl my-5 ml-3">{{ route.params.id }}</h1>
    <img
      :src="nasaImages[0].links[0].href"
      :alt="nasaImages[0].data[0].title"
      class="max-w-4xl w-full"
    />
    <p class="max-w-4xl mt-5">{{ nasaImages[0].data[0].description }}</p>
  </div>
</template>

<script>
import { ref, onBeforeMount } from 'vue';
import { useRoute } from 'vue-router';

export default {
  setup() {
    const nasaImages = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      fetch(`https://images-api.nasa.gov/search?q=${route.params.id}`)
        .then((response) => response.json())
        .then((data) => {
          nasaImages.value = data.collection.items;
          console.log(nasaImages.value);
        });
    });

    return { nasaImages, route };
  },
};
</script>

<style></style>
