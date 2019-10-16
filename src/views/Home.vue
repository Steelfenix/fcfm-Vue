<template>
  <div class="justify-center p-8">
    <ImageCard :image-data="imageData"></ImageCard>
  </div>
</template>

<script>
import ImageCard from '../components/ImageCard';

export default {
  name: 'home',
  components: {
    ImageCard
  },
  data() {
    return {
      imageData: {
        publishedDate: new Date(),
        url:
          'https://images.unsplash.com/photo-1556742393-d75f468bfcb0?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1950&q=80',
        downloads: 16817,
        camara: 'Canon EOS 5D Mark IV',
        user: {
          name: 'Adrián Castillo',
          profilePictureUrl:
            'https://images.unsplash.com/profile-1495427732560-fe5248ad6638?dpr=2&auto=format&fit=crop&w=150&h=150&q=60&crop=faces&bg=fff'
        }
      }
    };
  }
  // mounted() {
  //   this.$http
  //     .get(
  //       'https://api.unsplash.com/photos/?client_id=d9141a5df23f08e091fe5bde7245402a5af97fc843df78727755d6ccd3344e22'
  //     )
  //     .then(response => {
  //       console.log(response);
  //     });
  // }
};
</script>
