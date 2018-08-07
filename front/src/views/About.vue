<template>
  <div class="about">
    <h1>This is an about page</h1>
    <Patate msg="Test Patate"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Patate from '@/components/Patate.vue'

export default {
  name: 'about',
  components: {
    Patate
  }
}
</script>
