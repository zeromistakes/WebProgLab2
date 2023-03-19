<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  display: flex;
  flex-direction: row;
  width: 900px;
  height: 100vh;
  background: #c8c8c8;
  margin: 0 auto;
}

.leftWrapper {
  min-width: 200px;
  height: 100%;
  background: #6868c3;
  padding: 16px;
}

.rightWrapper {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  height: 100%;
  background: #89ec89;
}

.activeImageContainer {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: #7de5e5;
}

.imageConfig {
  width: 100%;
  height: 200px;
  background: #a2a2fb;
}
.configContainer {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>

<template>
  <div class="container">
    <div class="leftWrapper">
      <ImagesList
          :items="listItems"
          :activeImage="activeImage"
          @set-active-image-id="setActiveImage"
          @set-active-image-alt="setActiveAlt"
      />
    </div>
    <div class="rightWrapper">
      <div class="activeImageContainer">
        <ActiveImage
            :activeImage="activeImage"
            :activeWidth="+activeWidth"
            :activeHeight="+activeHeight"
            :activeBorder="+activeBorder"
            :activeAlt="activeAlt"
        />
      </div>
      <div class="imageConfig">
        <div class="configContainer">
          <label for="width">width: {{ activeWidth }}</label>
          <input
              type="range"
              name="width"
              class="width"
              v-model="activeWidth"
              max="500"
              min="50"
          >
          <label for="height">height: {{ activeHeight }}</label>
          <input
              type="range"
              name="height"
              class="height"
              v-model="activeHeight"
              max="500"
              min="50"
          >
          <label for="borderWidth">borderWidth: {{ activeBorder }}</label>
          <input
              type="range"
              name="borderWidth"
              class="borderWidth"
              v-model="activeBorder"
              max="20"
              min="1"
          >
          <label for="altText">altText: {{ activeAlt }}</label>
          <input
              type="text"
              name="altText"
              class="altText"
              v-model="activeAlt"
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ImagesList from '@/components/ImagesList'
import ActiveImage from '@/components/ActiveImage'

export default {
  name: 'App',
  components: {
    ImagesList,
    ActiveImage,
  },
  data() {
    return {
      activeImage: {
        id: 0,
        name: 'vue',
        url: '/assets/vue.png',
        alt: 'vue',
      },
      activeWidth: 500,
      activeHeight: 500,
      activeBorder: 1,
      activeAlt: 'vue',
      listItems: [
        {
          id: 0,
          name: 'vue',
          url: '/assets/vue.png',
          alt: 'vue',
        },
        {
          id: 1,
          name: 'react',
          url: '/assets/react.png',
          alt: 'react',
        },
        {
          id: 2,
          name: 'angular',
          url: '/assets/angular.png',
          alt: 'angular',
        },
        {
          id: 3,
          name: 'electron',
          url: '/assets/electron.png',
          alt: 'electron',
        },
        {
          id: 4,
          name: 'node',
          url: '/assets/node.png',
          alt: 'node',
        },
      ],
    }
  },
  methods: {
    setActiveImage(id) {
      this.activeImage = this.listItems.find((item) => item.id === id);
      console.log(this.activeImage);
    },
    setActiveAlt(alt) {
      this.activeAlt = alt;
    }
  }
}
</script>


