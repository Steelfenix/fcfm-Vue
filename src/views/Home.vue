<template>
  <div class="flex flex-row p-8 w-full overflow-x-auto -mx-4">
    <div class="pl-4" v-for="image in images" :key="image.id">
      <ImageCard :image-data="image"></ImageCard>
    </div>
  </div>
</template>

<script>
import ImageCard from '../components/ImageCard';
import { getData } from '../index';
export default {
  name: 'home',
  components: {
    ImageCard
  },
  data() {
    return {
      images: []
    };
  },
  mounted() {
    this.images = getData();
    // this.$http
    //   .get(
    //     'https://api.unsplash.com/photos/?client_id='
    //   )
    //   .then(response => {
    //     this.images = response.data;
    //   });
  }
};
</script>
