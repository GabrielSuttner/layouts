<!--
  For pages with minimal text
-->
<template>
  <div
    class="w-full bg-gray-100 break-words relative sm:flex items-center text-left px-8 pt-24 pb-8 sm:p-24"
    style="height: 90vh; word-break: break-word;"
  >
    <!-- Link to edit this layout. -->
    <button v-if="authorized" class="editBtn absolute left-0 top-0 m-2">
      <router-link :to="`/admin/layouts/${layout._id}`">
        <img src="/images/icons/Edit.svg" alt="Edit" width="25px" />
      </router-link>
    </button>

    <!-- 
      Mobile Styling
     -->
    <div class="sm:hidden">
      <!-- 
        Where layered color divs are displayed
      -->
      <!-- <div class="absolute bg-gray-400" style="top: 6rem; left: 2vw; width: 60vw; height: 53vh;"></div> -->
      <div
        class="overflow-hidden absolute h-full top-0 left-0 w-full"
        :class="{ 'bg-gray-700': !layout.imgPath }"
        style="opacity: 0.7;"
      >
        <img :src="layout.imgPath" class="h-full object-cover rounded-sm mx-auto" />
      </div>

      <!-- 
        Where all text is displayed
      -->
      <div class="relative w-full" style="">
        <h1>{{ layout.title }}</h1>
        <h3 class="my-2">{{ layout.subtitle }}</h3>
        <div v-html="layout.content"></div>
      </div>
    </div>

    <!-- 
      Desktop styling
     -->
    <div class="hidden sm:block">
      <!-- 
        Where layered color divs are displayed
      -->
      <div
        class="absolute bg-gray-400"
        style="top: 6rem; right: 24vw; width: 26vw; height: 53vh;"
      ></div>
      <div
        class="overflow-hidden absolute"
        :class="{ 'bg-gray-700': !layout.imgPath }"
        style="height: 73vh; width: 40%; top: 15vh; right: 5%;"
      >
        <img :src="layout.imgPath" class="h-full object-cover rounded-sm mx-auto" />
      </div>

      <!-- 
        Where all text is displayed
      -->
      <div class="relative">
        <h1>{{ layout.title }}</h1>
        <h3>{{ layout.subtitle }}</h3>
        <div v-html="layout.content"></div>
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
  mounted() {
    console.log('layout:', this.layout);
  },
};
</script>

<style></style>
