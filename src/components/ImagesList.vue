<style>
.imgList {
  width: 100%;
  height: fit-content;
  list-style: none;
}
.listItem {
  margin-bottom: 5px;
  font-size: 20px;
  cursor: pointer;
  text-align: center;
}

.listItem:hover {
  background: rgba(216, 216, 216, 0.5);
}

.listItemActive {
  background: #000000;
  color: #ffffff;
}
</style>

<template>
<ul class="imgList">
  <li
      :class="activeImage.id === item.id ? 'listItemActive listItem' : 'listItem'"
      v-for="item in items"
      :key="item.id"
      @click="setActiveImage(item.id, item.alt)"
  >
    {{ item.name }}
  </li>
</ul>
</template>

<script>
export default {
  name: 'ImagesList',
  props: {
    items: {
      type: Array,
    },
    activeImage: {
      type: Object
    }
  },
  data() {
    return {

    }
  },
  methods: {
    setActiveImage(id, alt) {
      this.$emit('set-active-image-id', id);
      this.$emit('set-active-image-alt', alt);
    }
  }
}
</script>