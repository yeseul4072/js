<template>
  <div>
    <li @click="onVideoClick" class="video-list-item list-group-item">
      <img :src="thumbnailUrl" class="mr-3" alt="Youtube thumnails image">
      <div class="media-body">
        {{ video.snippet.title }}
      </div>
      </li>
  </div>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: {
    video: Object
  },
  methods: {
    onVideoClick() {
      this.$emit('video-select', this.video)
    }
  },
  computed: {
    // 함수지만 명사 => 결국 리턴되는값이 사용되기 때문
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url
    }
  }
}
</script>

<style scoped>
li.video-list-item {
  display: flex;
  cursor: pointer;
}
li.video-list-item:hover {
  background-color: #eee;
}
.media-body {
  margin: auto 0;
}
</style>
