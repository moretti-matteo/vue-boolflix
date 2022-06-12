<template>
  <section>
    <h1>Series TV:</h1>
    <div class="container">
      <BaseCard v-for="serie in series" :key="serie.id" :title="serie.name" :originalTitle="serie.original_name"
        :overview="serie.overview" :poster="serie.poster_path" />
    </div>
  </section>
</template>

<script>
import BaseCard from '../card/BaseCard.vue';

export default {
    name: "SectionSeries",
    props: {
        series: []
    },
    components: { BaseCard }
}
</script>

<style lang="scss" scoped>
</style>