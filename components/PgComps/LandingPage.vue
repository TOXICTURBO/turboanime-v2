<template>
  <div>
    <!-- Popular Anime Carousel -->
    <v-carousel
      class="popular-carousel d-none d-md-block"
      hide-delimiters
      progress="green"
      height="320px"
      :show-arrows="false"
      :cycle="true"
    >
      <v-carousel-item
        v-for="(item, i) in popularData?.results"
        :key="i"
        :src="item.bannerImage"
        cover
      >
        <div class="carousel-item">
          <img :src="item.coverImage.large" alt="Carousel Image" />
          <div class="carousel-overlay"></div>
          <div class="carousel-content">
            <h2>{{ item.title.userPreferred }}</h2>
            <p class="text--secondary">{{ item.title.native }}</p>
            <p class="description">{{ item.description }}</p>
            <v-btn
              :to="'/anime/' + item.id"
              :color="item.coverImage.color ? item.coverImage.color : 'transparent'"
              class="read-more-btn"
            >
              Read more
            </v-btn>
          </div>
        </div>
      </v-carousel-item>
    </v-carousel>

    <!-- Trending and Popular Anime Grid -->
    <v-container>
      <!-- Trending Anime -->
      <h1 class="section-title">Trending Anime</h1>
      <v-row v-if="!trpend && !trenderr">
        <v-col
          v-for="(d, i) in trendingData?.results"
          :key="i"
          cols="12"
          sm="6"
          md="4"
          lg="3"
        >
          <AnimeCard :data="d" />
        </v-col>
      </v-row>
      <v-row v-else-if="trpend" class="loading-row">
        <v-progress-circular :size="45" indeterminate color="primary" />
      </v-row>
      <v-row v-else>
        <v-alert dense type="error" class="error-alert" title="Error" text="Error loading trending anime!" />
        <v-btn @click="trenddataRefresh()" class="reload-btn">
          Reload?
          <v-icon>mdi-reload</v-icon>
        </v-btn>
      </v-row>

      <!-- Popular Anime -->
      <h1 class="section-title">Popular Anime</h1>
      <v-row v-if="!popend && !poperr">
        <v-col
          v-for="(d, i) in popularData?.results"
          :key="i"
          cols="12"
          sm="6"
          md="4"
          lg="3"
        >
          <AnimeCard :data="d" />
        </v-col>
      </v-row>
      <v-row v-else-if="popend" class="loading-row">
        <v-progress-circular :size="45" indeterminate color="primary" />
      </v-row>
      <v-row v-else>
        <v-alert dense type="error" class="error-alert" title="Error" text="Error loading popular anime!" />
        <v-btn @click="popdataRefresh()" class="reload-btn">
          Reload?
          <v-icon>mdi-reload</v-icon>
        </v-btn>
      </v-row>
    </v-container>
  </div>
</template>

<style scoped>
.section-title {
  font-size: 24px;
  margin-bottom: 20px;
}

.popular-carousel {
  margin-bottom: 30px;
}

.carousel-item {
  position: relative;
}

.carousel-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}

.carousel-content {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: #fff;
  text-align: center;
  padding: 20px;
}

.carousel-content h2 {
  font-size: 24px;
  margin-bottom: 10px;
}

.carousel-content .description {
  font-size: 14px;
  margin-bottom: 20px;
}

.read-more-btn {
  color: #fff;
  background-image: linear-gradient(to right, #ff8a00, #e52e71);
  transition: background-color 0.3s;
}

.read-more-btn:hover {
  background-image: linear-gradient(to right, #ff8a00, #ff1358);
}

.loading-row {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
}

.error-alert {
  background-color: #ff5252;
  color: #fff;
}

.reload-btn {
  margin-top: 10px;
  color: #fff;
  background-image: linear-gradient(to right, #00b4db, #0083b0);
  transition: background-color 0.3s;
}

.reload-btn:hover {
  background-image: linear-gradient(to right, #00b4db, #0083b0);
}
</style>
