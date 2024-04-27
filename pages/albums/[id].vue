<script setup lang="ts">
type Album = {
    character: {
        name: string;
        image: string;
        status: string;
        id: string;
        species: string;
        location: {
            name: string
        }
    }
}

const route = useRoute()

const query = gql`
query getAlbum($id: ID!) {
  character(id: $id) {
      name
      image
      status
      id
      species
      location {
        name
      }
    }
}
  `
  const { data, error } = await useAsyncQuery<Character>(query, {
    id: route.params.id
  })
</script>

<template>
    <div>
      <NuxtLink to="/" class="ml-3">Back</NuxtLink>
      <AlbumCard
        :id="data.character.id"
        :name="data.character.name"
        :image="data.character.image"
        :status="data.character.status"
        :species="data.character.species"
        :location="data.character.location.name"
    />
    </div>
</template>