<template>
  <div
    class="mt-4 bg-white rounded-lg shadow-lg overflow-hidden"
    style="width:350px;"
  >
    <!-- <div
      class="h-64 bg-cover bg-center"
      :style="{ backgroundImage: `url('${imageData.urls.full}')` }"
    /> -->
    <img class="h-64 w-full object-cover" :src="imageData.urls.regular" />
    <div class="px-8 py-4">
      <div class="flex justify-between items-center">
        <div>
          <h4 class="text-2xl font-bold">Info</h4>
          <div class="text-lg font-hairline mt-1">{{ formatedDate }}</div>
          <div class="text-sm font-bold mt-1">{{ imageData.user.name }}</div>
        </div>
        <img
          @click="onClickUserImage"
          class="rounded-full h-16 cursor-pointer"
          :src="imageData.user.profile_image.medium"
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
        <span class="mt-1 text-3xl font-light">{{ imageData.likes }}</span>
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
          alt_description: '',
          created_at: '',
          description: '',
          id: '',
          likes: 0,
          camara: '',
          updated_at: new Date().toString(),
          urls: {
            raw: '',
            full: '',
            regular: '',
            small: '',
            thumb: ''
          },
          user: {
            id: '',
            updated_at: new Date().toString(),
            username: '',
            name: '',
            first_name: '',
            profile_image: {
              large: '',
              medium: '',
              small: ''
            }
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
  methods: {
    onClickUserImage() {
      this.$router.push({ path: `/user/${this.imageData.user.username}` });
    }
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
        new Date(this.imageData.created_at).getDate() +
        ' ' +
        monthNames[new Date(this.imageData.created_at).getMonth()] +
        ' ' +
        new Date(this.imageData.created_at).getFullYear()
      );
    }
  },
  mounted() {
    this.date = this.imageData.publishedDate;
  }
};
</script>
