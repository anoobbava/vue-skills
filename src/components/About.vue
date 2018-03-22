<template>
  <div class="about">
    <p>Hi {{ name1 }}, How are You ???</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        name1: this.$route.params.name
      }
    }
  };
</script>
