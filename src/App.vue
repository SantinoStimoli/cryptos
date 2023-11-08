<template>
  <main>
    <List :cryptos="cryptos" />
  </main>
</template>

<script>
import axios from 'axios'
import Search from './components/Search.vue'
import List from './components/List.vue'

export default {
  components: { Search, List },
  data () {
    return {
      cryptos: []
    }
  },
  methods: {
    async getCryptos () {
      const options = {
        method: 'GET',
        url: 'https://coinranking1.p.rapidapi.com/coins',
        params: {
          referenceCurrencyUuid: 'yhjMzLPhuIDl',
          timePeriod: '24h',
          'tiers[0]': '1',
          orderBy: 'marketCap',
          orderDirection: 'desc',
          limit: '50',
          offset: '0'
        },
        headers: {
          'X-RapidAPI-Key':
            '98715c9804msh27b7e791e2e5d85p16091bjsnba36cbd2c1e4',
          'X-RapidAPI-Host': 'coinranking1.p.rapidapi.com'
        }
      }

      try {
        const response = await axios.request(options)
        this.cryptos = response.data.data.coins
        console.log(this.cryptos[0])
      } catch (error) {
        // console.error(error)
      }
    }
  },
  created () {
    this.getCryptos()
  }
}
</script>
