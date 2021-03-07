  
<template>
  <div>
    <router-link :to="`/About/${this.id}`">
      <div>
        <b-card
          :title="name"
          :img-src="img"
          img-alt="Image"
          img-top
          tag="article"
          style="max-width: 20rem;"
          class="mb-2"
        >
          <b-card-text> </b-card-text>
        </b-card></div></router-link>
  </div>
</template>

<script>
export default {
  props: {
    id:Number,
    name: String,
    img: String,
  },
};
</script>

<style></style>
