<template>
<!-- test -->
  <div class="w-full p-6 pb-12 md:px-20 md:py-12 relative" :class="getBackGround()">
    <!-- Link to edit this layout. -->
    <button v-if="authorized" class="editBtn absolute left-0 top-0 m-2">
      <router-link :to="`/admin/layouts/${layout._id}`">
        <img src="/images/icons/Edit.svg" alt="Edit" width="25px" />
      </router-link>
    </button>
    <div class="md:grid md:grid-cols-2 gap-24">
      <div class="md:col-span-1 md:h-96 lg:h-128 md:my-auto md:mx-auto overflow-hidden rounded-sm shadow-md hidden md:block">
        <img :src="layout.imgPath" alt="" class="object-cover h-full w-full" />
      </div>
      <div class="md:col-span-1 flex items-center my-4">
        <div>
          <h1 class="font-medium">{{ layout.title }}</h1>
          <p v-html="layout.content"></p>
          <button
            v-if="layout.button"
            @click="goToEnrollNow"
            class="btn-action rounded-full md:rounded w-full md:w-32 h-12 my-8 md:my-6 md:h-auto"
          >
            Enroll Now
          </button>
        </div>
      </div>
      <div class="overflow-hidden rounded-sm shadow-md md:hidden">
        <img :src="layout.imgPath" alt="" class="object-cover h-full w-full" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    layout: Object,
    index: Number,
  },
  computed: {
    authorized() {
      return this.$store.state.authorized;
    },
  },
  methods: {
    getBackGround() {
      if (this.index % 2) {
        return 'bg-gray-200';
      }
      return 'bg-white';
    },
    goToEnrollNow() {
      if (this.layout.page === 'Retail Info') {
        this.$router.push({ path: '/user', params: { initialShowRegister: true } });
      } else {
        this.$router.push({ path: '/commercial' });
      }
    },
  },
  mounted() {
    console.log('layout:', this.layout);
  },
};
</script>
<style scoped></style>
