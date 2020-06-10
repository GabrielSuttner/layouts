<!--
  For pages with a wall of text
-->
<template>
  <div
    class="w-full bg-gray-100 break-words pb-20 relative text-left"
    style="min-height: 100vh; word-break: break-word;"
  >
    <!-- Link to edit this layout. -->
    <button v-if="authorized" class="editBtn absolute left-0 top-0 m-2">
      <router-link :to="`/admin/layouts/${layout._id}`">
        <img src="/images/icons/Edit.svg" alt="Edit" width="25px" />
      </router-link>
    </button>

    <div
      class="heroHeader flex items-center justify-center w-full px-10"
      :class="{ 'bg-blue-glow-light': !layout.imgPath }"
      :style="setBackground"
      style="height: 15vh;"
    >
      <h1 class="text-black">{{ layout.title }}</h1>
    </div>

    <!-- <div class="overflow-hidden absolute" :class="{'bg-gray-700': !layout.imgPath}" style="height:73vh; width:40%; top:15vh; right:5%;">
      <img :src="layout.imgPath" class="h-full object-cover rounded-sm mx-auto"/>
    </div> -->
    <div class="px-8 sm:px-24 text-left md:w-8/12 md:mx-auto">
      <div><img :src="layout.imgurl" /></div>
      <div v-html="layout.content"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    layout: Object,
  },
  computed: {
    setBackground() {
      if (this.layout.imgPath) {
        return 'background-image: url(' + this.layout.imgPath + ')';
      } else {
        return '';
      }
    },
    authorized() {
      return this.$store.state.authorized;
    },
  },
};
</script>

<style>
.heroHeader {
  position: relative;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  filter: opacity(0.9);
}
</style>
