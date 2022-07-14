<template>
  <div class="details">
    <h2>{{ route.params.id }}</h2>
    <img
      :src="nasaImages[0].links[0].href"
      :alt="nasaImages[0].data[0].title"
    />
    <p>{{ nasaImages[0].data[0].description }}</p>
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
