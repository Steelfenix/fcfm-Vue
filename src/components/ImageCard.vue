<template>
  <div class="bg-white rounded-lg shadow overflow-hidden max-w-sm m-w-full">
    <img :src="imageData.url" />
    <div class="px-8 py-4">
      <div class="flex justify-between items-center">
        <div>
          <h4 class="text-2xl font-bold">Info</h4>
          <div class="text-lg font-hairline mt-1">{{ formatedDate }}</div>
          <div class="text-sm font-bold mt-1">{{ imageData.user.name }}</div>
        </div>
        <img
          class="rounded-full h-16"
          :src="imageData.user.profilePictureUrl"
        />
      </div>
      <div class="flex mt-8 flex-col">
        <div class="flex text-xl items-center">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            width="24"
            height="24"
            class="h-8 w-8"
          >
            <path
              d="M11 14.59V3a1 1 0 0 1 2 0v11.59l3.3-3.3a1 1 0 0 1 1.4 1.42l-5 5a1 1 0 0 1-1.4 0l-5-5a1 1 0 0 1 1.4-1.42l3.3 3.3zM3 17a1 1 0 0 1 2 0v3h14v-3a1 1 0 0 1 2 0v3a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-3z"
            />
          </svg>
          <p class="ml-1">Downloads</p>
        </div>
        <span class="mt-1 text-lg font-light">{{ imageData.downloads }}</span>
      </div>
      <div class="flex mt-3 items-center">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
          width="24"
          height="24"
          class="h-8 w-8"
        >
          <path
            d="M20 7a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V9c0-1.1.9-2 2-2h2.38l1.73-3.45A1 1 0 0 1 9 3h6a1 1 0 0 1 .9.55L17.61 7H20zM9.62 5L7.89 8.45A1 1 0 0 1 7 9H4v10h16V9h-3a1 1 0 0 1-.9-.55L14.39 5H9.62zM12 17a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm0-2a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
          />
        </svg>
        <p class="ml-1 font-light text-base">
          {{ imageData.camara }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'image-card',
  props: {
    imageData: {
      type: Object,
      default: function() {
        return {
          publishedDate: new Date(),
          url: '',
          downloads: 0,
          camara: '',
          user: {
            name: '',
            profilePictureUrl: ''
          }
        };
      }
    }
  },
  data() {
    return {
      date: new Date()
    };
  },
  computed: {
    formatedDate() {
      const monthNames = [
        'January',
        'February',
        'March',
        'April',
        'May',
        'June',
        'July',
        'August',
        'September',
        'October',
        'November',
        'December'
      ];

      return (
        this.date.getDate() +
        ' ' +
        monthNames[this.date.getMonth()] +
        ' ' +
        this.date.getFullYear()
      );
    }
  },
  mounted() {
    this.date = this.imageData.publishedDate;
  }
};
</script>
<style></style>
