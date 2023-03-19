<template>
  <div>
    <img
        :src="activeImage.url" :alt="activeAlt"
        :style="`width: ${activeWidth}px; height: ${activeHeight}px; border: ${activeBorder}px solid #000000`"
    />
    <div>altText: {{activeAlt}}</div>
  </div>
</template>

<script>
export default {
  name: "ActiveImage",
  props: {
    activeImage: {
      type: Object
    },
    activeWidth: {
      type: Number
    },
    activeHeight: {
      type: Number
    },
    activeBorder: {
      type: Number
    },
    activeAlt: {
      type: String
    },
  },
  data() {
    return {

    }
  }
}
</script>

<style scoped>

</style>