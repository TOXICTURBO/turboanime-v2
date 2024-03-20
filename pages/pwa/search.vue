<script setup>
import debounce from "lodash.debounce";
import axios from "axios";

const env = useRuntimeConfig();
const searchResults = ref();
const search = ref();
const searchLoading = ref(true);

useHead({
  htmlAttrs: {
    lang: "en",
  },
  title: "Search Anime",
});

const selectGenres = ref();
const selectTags = ref();

const genreItems = [
  "Action", "Adventure", "Comedy", "Drama", "Ecchi", "Fantasy", "Horror", "Mahou Shoujo", "Mecha", "Music",
  "Mystery", "Psychological", "Romance", "Sci-Fi", "Slice of Life", "Sports", "Supernatural", "Thriller", "Hentai"
];
const tagItems = [
  // Tags array
];

const debouncedSearch = debounce(async () => {
  try {
    const { data } = await axios.post(
      `${env.public.API_URL}/api/${env.public.version}/search`,
      {
        search: search.value,
        genres: selectGenres.value,
        tags: selectTags.value,
      }
    );
    searchResults.value = data;
    searchLoading.value = false;
  } catch (error) {
    console.error("Error occurred while searching:", error);
  }
}, 200);

const query = useRoute().query;

if (query.q || query.genres || query.tags) {
  search.value = query?.q;
  selectGenres.value =
    query?.genres && query?.genres.includes(",") ? query?.genres.split(",") : query?.genres;
  selectTags.value =
    query?.tags && query?.tags.includes(",") ? query?.tags.split(",") : query?.tags;
  debouncedSearch();
}
</script>

<template>
  <v-breadcrumbs>
    <template #prepend>
      <v-icon size="small" icon="mdi-home"></v-icon>
    </template>
    <v-breadcrumbs-item title="Home" to="/pwa" />
    <v-breadcrumbs-divider />
    <v-breadcrumbs-item title="Search" />
  </v-breadcrumbs>
  <v-container>
    <h1 class="mb-2">Search Anime</h1>
    <v-text-field
      v-model="search"
      variant="solo"
      color="green"
      label="Search Anime"
      flat
      clearable
      single-line
      hide-details
      prepend-inner-icon="mdi-magnify"
      @update:model-value="debouncedSearch"
    />
    <v-row class="my-1">
      <v-col style="padding-bottom: 0" cols="12" sm="6">
        <v-combobox
          v-model="selectGenres"
          :items="genreItems"
          variant="solo"
          label="Genres"
          multiple
          @update:model-value="debouncedSearch"
        ></v-combobox>
      </v-col>
      <v-col style="padding-bottom: 0" cols="12" sm="6">
        <v-combobox
          v-model="selectTags"
          :items="tagItems"
          variant="solo"
          label="Tags"
          multiple
          @update:model-value="debouncedSearch"
        ></v-combobox>
      </v-col>
    </v-row>
    <v-card class="mt-4">
      <v-card-text>
        <div v-if="!searchResults?.results">
          <div class="loadingBlock">
            <v-icon size="5rem">mdi-magnify</v-icon>
            <h2>Search Anime</h2>
          </div>
        </div>
        <v-progress-linear v-else-if="searchLoading" indeterminate />
        <v-list v-else lines="two">
          <v-list-item title="Search result" />
          <v-divider />
          <v-list-item
            v-for="item in searchResults.results"
            :key="item.id"
            :to="'/anime/' + item.id"
          >
            <template #prepend>
              <img
                v-if="item.coverImage.medium"
                :src="item.coverImage.medium"
                :alt="item.id + '_img'"
                class="mr-3"
                style="border-radius: 4px; width: 60px; height: 10%"
              />
            </template>
            <v-list-item-title>{{ item.title.userPreferred }}</v-list-item-title>
            <v-list-item-subtitle>
              Episode {{ item.episodes }} /
              {{
                item.status === "FINISHED" ? "Finished" :
                item.status === "RELEASING" ? "Currently Releasing" :
                item.status === "NOT_YET_RELEASED" ? "Not Released" :
                item.status === "CANCELLED" ? "Cancelled" :
                "No data"
              }}
            </v-list-item-subtitle>
            <template #append>
              <v-icon color="yellow">mdi-star</v-icon>
              {{ item.averageScore / 10 }}
            </template>
          </v-list-item>
        </v-list>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<style>
.loadingBlock {
  height: 100vh;
  display: grid;
  place-items: center;
}
</style>
