<template>
  <div class="flex flex-row justify-center  w-full ">
    <div
      class="flex flex-col items-center bg-white w-4/5 h-auto mt-32 py-8 px-16 rounded-lg shadow-lg lg:flex-row"
    >
      <img class="rounded-full w-56 block" :src="user.profile_image.large" />
      <div class="flex flex-col lg:ml-16">
        <div
          class="text-3xl text-center leading-none sm:2xl lg:text-6xl text-gray-900"
        >
          {{ user.name }}
        </div>
        <div class="flex justify-between">
          <div class="flex text-lg font-bold text-gray-700">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              width="24"
              height="24"
            >
              <path
                d="M5.64 16.36a9 9 0 1 1 12.72 0l-5.65 5.66a1 1 0 0 1-1.42 0l-5.65-5.66zm11.31-1.41a7 7 0 1 0-9.9 0L12 19.9l4.95-4.95zM12 14a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm0-2a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
              />
            </svg>
            <span class="ml-2">{{ user.location }}</span>
          </div>
          <div class="flex text-lg font-bold text-gray-700 ml-4">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              width="24"
              height="24"
            >
              <path
                d="M4.06 13a8 8 0 0 0 5.18 6.51A18.5 18.5 0 0 1 8.02 13H4.06zm0-2h3.96a18.5 18.5 0 0 1 1.22-6.51A8 8 0 0 0 4.06 11zm15.88 0a8 8 0 0 0-5.18-6.51A18.5 18.5 0 0 1 15.98 11h3.96zm0 2h-3.96a18.5 18.5 0 0 1-1.22 6.51A8 8 0 0 0 19.94 13zm-9.92 0c.16 3.95 1.23 7 1.98 7s1.82-3.05 1.98-7h-3.96zm0-2h3.96c-.16-3.95-1.23-7-1.98-7s-1.82 3.05-1.98 7zM12 22a10 10 0 1 1 0-20 10 10 0 0 1 0 20z"
              />
            </svg>
            <span class="ml-2">{{ user.portfolio_url }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { getUser } from '../index';

export default {
  data() {
    return {
      user: {
        name: 'Jhon Doe',
        location: 'Not Yet!!',
        portfolio_url: '',
        profile_image: {
          large: ''
        }
      }
    };
  },
  mounted() {
    // this.$http
    //   .get(
    //     `https://api.unsplash.com/users/${this.$route.params.id}?client_id=`
    //   )
    //   .then(response => {
    //     this.user = response.data;
    //   });
    this.user = getUser();
    console.log(this.$route.params.id);
  }
};
</script>
