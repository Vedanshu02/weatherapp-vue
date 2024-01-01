<script lang="ts">
import { defineComponent, ref } from 'vue'

import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default defineComponent({
  props: ['data'],
  setup(props) {
    const temp = ref(props.data.temp)
    const hum = ref(props.data.humidity)

    return { temp, hum }
  }
})
</script>

<template>
  <div class="card" style="width: 18rem">
    <ul class="list-group list-group-flush">
      <li class="list-group-item">Temperature:{{ temp }}</li>
      <li class="list-group-item">Humidity:{{ hum }}</li>
    </ul>
  </div>
</template>

<style scoped>
.card {
  margin-top: 50px;
  width: fit-content;
}
</style>