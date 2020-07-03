<template>
  <div class="w-full p-4 md:p-8" :class="getBackGround()">
    <!-- Link to edit this layout. -->
    <button v-if="authorized" class="editBtn absolute left-0 top-0 m-2">
      <router-link :to="`/admin/layouts/${layout._id}`">
        <img src="/images/icons/Edit.svg" alt="Edit" width="25px" />
      </router-link>
    </button>
    <div class="md:grid md:grid-cols-5">
      <div class="col-span-3 flex items-center my-4">
        <div>
          <h2>{{ layout.title }}</h2>
          <p v-html="layout.content"></p>
          <button v-if="layout.button" @click="goToEnrollNow" class="btn-action">Enroll Now</button>
        </div>
      </div>
      <div class="col-span-2 md:p-8">
        <img :src="layout.imgPath" alt="" />
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
