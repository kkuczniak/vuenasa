<template>
  <div
    v-for="nasaImage in nasaImages"
    :key="nasaImage.id"
    class="homeComponent text-white w-full max-w-xl md:border md:border-white mt-3 lg:mt-5 flex flex-col"
  >
    <h3
      class="text-2xl text-white font-Nunito font-semibold tracking-wider pl-2 mb-2 md:mb-4 md:mt-1"
    >
      {{ nasaImage.data[0].title }}
    </h3>
    <p class="font-Nunito font-light tracking-wide px-5 mb-2">
      {{ nasaImage.data[0].description }}
    </p>
    <img :src="nasaImage.links[0].href" alt="{{index}}" />
    <router-link
      :to="'/nasa/' + nasaImage.data[0].nasa_id"
      class="flex justify-center"
    >
      <button
        class="border border-white rounded text-white uppercase px-2 my-2 hover:bg-[#ffffff3f]"
      >
        Read more
      </button>
    </router-link>
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
