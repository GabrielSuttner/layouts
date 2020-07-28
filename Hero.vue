<template>
  <div class="sm:grid sm:grid-cols-2 relative cursor-pointer" @click="route">
    <!-- link to edit this layout -->
    <button
      v-if="authorized"
      @click.stop="$router.push({ path: `/admin/layouts/${layout._id}` })"
      class="editBtn absolute top-0 left-0 m-2"
    >
      <img src="/images/icons/Edit.svg" alt="Edit" width="25px" />
    </button>
    <!-- Image -->
    <div
      class="overflow-hidden opacity-60 sm:opacity-100"
      :style="`background-image: url(${layout.imgPath}; background-position: center; background-size: cover; height:400px`"
    ></div>

    <!-- Text -->
    <div
      class="text-left font-semibold absolute sm:relative bottom-2 left-1 right-1 sm:bottom-auto sm:left-auto sm:right-auto text-black sm:text-neutral-darkest sm:flex sm:items-center sm:px-8"
    >
      <div>
        <h1>{{ layout.title }}</h1>
        <h3 v-html="layout.content"></h3>
      </div>
    </div>
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
  methods: {
    route() {
      if (this.layout.link == null) {
        return;
      }
      if (this.layout.link.includes('{')) {
        //for objects
        const link = JSON.parse(this.layout.link);
        this.$router.push(link);
        return;
      }
      location.href = this.layout.link;
    },
  },
};
</script>

<style></style>
