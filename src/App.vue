<script setup>
import { ref, computed, onMounted } from 'vue';

const images = ref([
  'https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60',
  'https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60',
  'https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60',
  'https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60'
  ]);

const currentIndex = ref(0);

const currentImage = computed(() => images.value[currentIndex.value]);

const nextImage = () => {
  currentIndex.value = (currentIndex.value + 1) % images.value.length;
};

const prevImage = () => {
  currentIndex.value = (currentIndex.value - 1 + images.value.length) % images.value.length;
};


onMounted(() => {
  setInterval(nextImage, 3000);
});

</script>
<template>
  <div class="app">
    <div class="image-carousel">
      <div class="carousel">
        <img :src="currentImage" alt="Carousel Image" class="w-full h-full object-cover">
      </div>
      <div class="controls mt-3 flex">
        <button  @click="prevImage" :disabled="currentIndex === 0" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-l mr-3">Previous</button>
        <button  @click="nextImage" :disabled="currentIndex === images.length - 1" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-r">Next</button>
      </div>
    </div>
  </div>
</template>



<style>

.app {
 
}

.image-carousel img{
  height: 600px;
  width: 1000px;
}

.carousel {
  /* Your custom styles for the carousel content */
}

.controls {
  /* Your custom styles for the carousel controls */
}
</style>
