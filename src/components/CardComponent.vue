<template>
  <div class="homeComponent w-full h-48 bg-gray-600">
    <div v-for="nasaImage in nasaImages" :key="nasaImage.id">
      <router-link :to="'/nasa/' + nasaImage.data[0].nasa_id">
        <h3 class="text-2xl text-white">{{ nasaImage.data[0].title }}</h3>
        <p>{{ nasaImage.data[0].description }}</p>
        <img :src="nasaImage.links[0].href" alt="{{index}}" />
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  props: ['nasaImages'],
  setup(props) {
    console.log(props.nasaImages);
  },
};
</script>

<style></style>
