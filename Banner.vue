<template>
  <div class="relative w-full text-black text-center z-1 shadow-lg">
    <button v-if="authorized" class="editBtn absolute left-0 top-0 m-2">
      <router-link :to="`/admin/layouts/${layout._id}`">
        <img src="/images/icons/Edit.svg" alt="Edit" width="25px" />
      </router-link>
    </button>
    <router-link
      class="absolute left-0 ml-2 sm:ml-0 sm:left-2 top-1 text-white hover:text-neutral"
      to="/"
    >
      <font-awesome-icon class="mr-2 text-xl -mb-px" icon="home" /><span
        class="hidden sm:inline-block"
      >
        Home
      </span>
    </router-link>

    <!-- <div class="bg-primary py-4 px-10 font-medium text-white" v-html="layout.content"></div> -->
    <div class="bg-feedbackError py-4 px-10 font-medium text-white">
      This site is currently under construction. No pricing is final.
    </div>

    <a
      href="tel:8014104998"
      class="absolute right-0 mr-2 sm:mr-0 sm:right-2 top-1 text-white hover:text-neutral"
    >
      <font-awesome-icon class="mr-2 text-xl -mb-px" icon="phone-alt" />
      <span class="hidden sm:inline-block">(801) 410-4998</span>
    </a>
  </div>
</template>

<script>
export default {
  props: {
    layout: Object,
  },
  computed: {
    authorized() {
      return this.$store.state.authorized;
    },
  },
};
</script>

<style></style>
