<template>
  <div>
    <AlbumCard
      v-for="{ id, name, image, status, species, location } in data.characters
        .results"
      :key="id"
      :id="id"
      :name="name"
      :image="image"
      :status="status"
      :species="species"
      :location="location.name"
    />
  </div>
</template>
<script lang="ts" setup>
type AlbumsResults = {
  characters: {
    results: {
      id: string;
      name: string;
      image: string;
      status: string;
      species: string;
      location: {
        name: string;
      };
    }[];
  };
};
const query = gql`
  query getPhotos {
    characters {
      results {
        name
        image
        id
        status
        type
        species
        location {
          name
        }
      }
    }
  }
`;
const { data } = await useAsyncQuery<AlbumsResults>(query);
</script>
