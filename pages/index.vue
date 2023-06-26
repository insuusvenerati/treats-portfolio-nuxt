<script setup lang="ts">
import { ImagesResponse } from "~/types/images";

useHead({
  titleTemplate: (title) => `${title} | bg`,
});

const { findOne } = useStrapi();
const { data: images } = await useAsyncData(
  "bg",
  () =>
    findOne("bg", {
      populate: {
        images: {
          fields: ["url", "name"],
        },
      },
    }) as Promise<ImagesResponse>,
  {
    lazy: false,
    transform: ({ data }) => {
      return { data: data.attributes.images.data };
    },
  }
);
</script>

<template>
  <div class="grid grid-cols-2 gap-4">
    <div v-for="(image, index) in images?.data">
      <a :href="image.attributes.url">
        <img
          class="object-cover rounded-md hover:brightness-110 hover:cursor-zoom-in w-[650px] h-[450px]"
          :src="image.attributes.url"
          :alt="image.attributes.name" />
      </a>
    </div>
  </div>
</template>
