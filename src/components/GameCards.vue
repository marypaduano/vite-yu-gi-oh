<template>
    <li class="card">
      <img :src="card.image_url" alt="">
      <h4 class="card_name">{{ card.name }}</h4>
      <span class="archetype">{{ card.archetype }}</span>
    </li>
</template>

    <script>
  export default {
    props: {
      card: {
        type: Object,
        required: true
      },
    }
  }
</script>

<style lang="scss" scoped>
.card {
  text-align: center;
  background-color: goldenrod;
  font-size: 15px;
  padding: 10px;
}

.card_name{
  text-transform: uppercase;
  color: white;
  font-weight: 600;
  padding-bottom: 30px;

}
</style>