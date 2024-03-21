<template>
  <div>
    <div class="flex items-center justify-between lg-gap-3 px-5 z-40">
      <h1 class="font-karla text-20px font-bold">Characters</h1>
      <div v-if="info.length > 6" class="cursor-pointer font-karla" @click="showAll = !showAll">
        {{ showAll ? 'show less' : 'show more' }}
      </div>
    </div>

    <!-- for bigger devices -->
    <div class="hidden md-grid w-full grid-cols-1 gap-10px md-gap-4 md-grid-cols-3 md-pt-7 md-pb-5 px-3 md-px-5 pt-4">
      <div v-for="(item, index) in displayedInfo" :key="index" class="md-hover-scale-1.02 snap-start hover-shadow-lg scale-100 transition-transform duration-200 ease-out w-full cursor-default">
        <div class="text-gray-300 space-x-4 col-span-1 flex w-full h-24 bg-secondary rounded-md overflow-hidden">
          <div class="relative h-full w-20">
            <img :src="getImageUrl(item)" :alt="getAltText(item)" class="h-full object-cover" />
          </div>
          <div class="py-2 flex flex-col justify-between">
            <p class="font-semibold">{{ getItemName(item) }}</p>
            <p>{{ item.role }}</p>
          </div>
        </div>
      </div>
    </div>

    <!-- for smaller devices -->
    <div class="flex md-hidden h-full w-full select-none overflow-x-scroll overflow-y-hidden scrollbar-hide gap-4 pt-8 pb-4 px-5 z-30">
      <div v-for="(item, index) in displayedInfo" :key="index" class="flex flex-col gap-3 shrink-0 cursor-pointer">
        <div class="hover-scale-105 hover-shadow-lg duration-300 ease-out group relative">
          <div class="h-190px w-135px rounded-md z-30">
            <img :src="getImageUrl(item)" :alt="getAltText(item)" class="z-20 h-190px w-135px object-cover rounded-md brightness-90" />
          </div>
        </div>
        <div class="w-135px lg-w-185px line-clamp-2">
          <h1 class="font-karla font-semibold text-15px">{{ getItemName(item) }}</h1>
          <h1 class="font-karla float-right italic text-12px">~{{ item.role }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    info: Array
  },
  data() {
    return {
      showAll: false
    };
  },
  computed: {
    displayedInfo() {
      return this.showAll ? this.info : this.info.slice(0, 6);
    }
  },
  methods: {
    getImageUrl(item) {
      return item.node.image.large || item.node.image.medium;
    },
    getAltText(item) {
      return item.node.name.userPreferred || item.node.name.full || "Character Image";
    },
    getItemName(item) {
      return item.node.name.full || item.node.name.userPreferred;
    }
  }
};
</script>

<style scoped>
/* Add your custom CSS styles here */

/* Example styles for larger devices */
@media (min-width: 768px) {
  .lg-gap-3 {
    gap: 0.75rem;
  }

  .text-20px {
    font-size: 1.25rem;
  }

  /* Add more styles for larger devices as needed */
}

/* Example styles for smaller devices */
@media (max-width: 767px) {
  .md-hidden {
    display: none;
  }

  /* Add more styles for smaller devices as needed */
}
</style>
