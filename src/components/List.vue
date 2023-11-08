<template>
  <DataTable :value="cryptos" paginator :rows="5" tableStyle="min-width: 50rem">
    <Column field="rank" header="Rank"></Column>
    <Column header="Image">
      <template #body="slotProps">
        <img :src="slotProps.data.iconUrl" class="w-6" />
      </template>
    </Column>
    <Column field="name" header="Name"></Column>
    <Column field="price" header="Price">
      <template #body="slotProps">
        {{ slotProps.data.price }}
      </template>
    </Column>
    <Column field="category" header="Category"></Column>
    <template #footer>
      In total there are {{ cryptos ? cryptos.length : 0 }} cryptos.
    </template>
  </DataTable>
</template>
<script>
export default {
  data () {
    return {
      cryptosF: []
    }
  },
  props: {
    cryptos: {
      type: Array,
      default: []
    }
  }
}
</script>
