<script lang="ts" setup>
const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  image: {
    type: String,
    required: true,
  },
  status: {
    type: String,
    required: true,
  },
  id: {
    type: String,
    required: true,
  },
  species: {
    type: String,
    required: true,
  },
  location: {
    type: String,
    required: true,
  },
});

const grayScaleWhenDead = computed(() =>
  props.status === 'Dead' ? { grayscale: true } : {}
);
</script>

<template>
  <div class="flex flex-wrap m-3 bg-gray-300 rounded-xl">
    <NuxtLink
      :to="`/albums/${id}`"
      class="flex justify-center w-full sm:w-1/2 md:w-1/3 lg:w-1/4 xl:w-1/4"
    >
      <NuxtImg
        :src="image"
        width="400"
        height="200"
        class="rounded-xl"
        :modifiers="grayScaleWhenDead"
      />
      <div class="m-3">
        <h3 class="text-xl mb-3">{{ name }}</h3>
        <p>Status: {{ status }}</p>
        <p>Species: {{ species }}</p>
        <p>Location: {{ location }}</p>
      </div>
    </NuxtLink>
  </div>
</template>
