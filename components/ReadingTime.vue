<template>
  <span v-if="{ time } > 1">~{{ time }} mins read</span>
  <span v-else>~{{ time }} min read</span>
</template>

<script>
export default {
  name: 'ReadingTime',
  data: function () {
    return {}
  },
  props: {
    time: {
      type: Number,
      default: 0
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss"></style>
