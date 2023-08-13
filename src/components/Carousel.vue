<script setup>
import { onMounted, onBeforeUnmount } from "vue";

const images = [
  "https://cdn.pixabay.com/photo/2014/02/27/16/10/flowers-276014_1280.jpg",
  "https://cdn.pixabay.com/photo/2018/01/14/23/12/nature-3082832_1280.jpg",
  "https://cdn.pixabay.com/photo/2015/12/01/20/28/road-1072823_1280.jpg",
  "https://cdn.pixabay.com/photo/2012/03/01/00/55/flowers-19830_1280.jpg",
];

let myCarousel;

onMounted(() => {
  const elem = document.getElementById("my-carousel");
  myCarousel = new Flickity(elem, {
    cellAlign: "left",
    contain: true,
    imagesLoaded: true,
  });
});

onBeforeUnmount(() => {
  myCarousel.destroy();
});
</script>

<template>
  <div class="max-w-[720px] mx-auto py-8 px-4">
    <div id="my-carousel">
      <div class="carousel-cell" v-for="(image, idx) in images" :key="idx">
        <img :src="image" alt="" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.carousel-cell.is-selected {
  height: 100%;
}

.carousel-cell.is-selected img {
  height: 100%;
}

:deep(.flickity-prev-next-button.previous),
:deep(.flickity-prev-next-button.next) {
  background-color: white;
}

:deep(.flickity-prev-next-button.previous) {
  left: 24px;
}

:deep(.flickity-prev-next-button.next) {
  right: 24px;
}

:deep(.flickity-page-dots) {
  bottom: -32px;
}
</style>
