<template>
  <div>
    <hash-loader :loading="isLoading" :color="'#68d391'" :size="100" />
    <px-assets-table v-if="!isLoading" :assets="assets" />
  </div>
</template>

<script>
import api from '@/api'
import PxAssetsTable from '@/components/PxAssetsTable'
import { HashLoader } from '@saeris/vue-spinners'
export default {
  name: 'Home',
  components: { PxAssetsTable, HashLoader },
  data() {
    return {
      isLoading: true,
      assets: []
    }
  },

  created() {
    this.isLÑoading = true

    api
      .getAssets()
      .then(assets => (this.assets = assets))
      .finally(() => (this.isLoading = false))
  }
}
</script>
