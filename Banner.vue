<template>
  <div class="relative w-full text-white text-center z-1 shadow-lg">
    <button v-if="authorized" class="editBtn absolute left-0 top-0 m-2">
      <router-link :to="`/admin/layouts/${layout._id}`">
        <img src="/images/icons/Edit.svg" alt="Edit" width="25px" />
      </router-link>
    </button>
    <button class="absolute text-xl right-0 top-0 iconBtn sm:m-1" @click="$emit('close')">
      <font-awesome-icon icon="times" />
    </button>
    <div class="bg-primary py-4 pr-10 pl-3 font-medium text-white" v-html="layout.content"></div>
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
