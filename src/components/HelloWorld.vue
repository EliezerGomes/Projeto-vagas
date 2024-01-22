<template>
  <div>
    {{ valor }}
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup() {
    const valor = ref('teste')

    return { valor }
  }
}
</script>