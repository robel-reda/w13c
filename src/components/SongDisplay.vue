<template>
  <div class="music-layout">


<!-- LEFT: PLAYLIST -->
<section class="playlist">

  <div class="section-heading">
    <div>
      <p class="small-title">YOUR COLLECTION</p>
      <h2>My Playlist</h2>
    </div>

    <span class="song-count">{{ songs.length }} Songs</span>
  </div>

  <!-- SONG ITEMS -->
  <div
    v-for="song in songs"
    :key="song.song_id"
    class="song-item"
    :class="{ active: currentSong && currentSong.song_id === song.song_id }"
    @click="$emit('select-song', song)"
  >

    <img
      :src="song.image_url"
      :alt="song.title"
      class="song-image"
    >

    <div class="song-details">
      <h3>{{ song.title }}</h3>
      <p>{{ song.artist }}</p>
    </div>

    <span class="play-button">▶</span>

  </div>

</section>


<!-- RIGHT: NOW PLAYING -->
<section class="now-playing">

  <p class="small-title">NOW PLAYING</p>

  <div v-if="currentSong" class="playing-content">

    <img
      :src="currentSong.image_url"
      :alt="currentSong.title"
      class="album-cover"
    >

    <h2>{{ currentSong.title }}</h2>

    <p class="artist-name">{{ currentSong.artist }}</p>

    <div class="music-bar">
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      <span></span>
    </div>

    <div class="control-buttons">
      <span>⏮</span>
      <span class="main-play">▶</span>
      <span>⏭</span>
    </div>

    <p class="status">♪ CURRENTLY SELECTED</p>

  </div>


  <!-- NO SONG SELECTED -->
  <div v-else class="empty-state">

    <div class="empty-icon">♫</div>

    <h2>Nothing Playing</h2>

    <p>
      Your next favorite song is waiting.
      Choose a track from your playlist.
    </p>

  </div>

</section>


  </div>
</template>

<script>

export default {

  name: "SongDisplay",

  props: {

    songs: {
      type: Array,
      required: true
    },

    currentSong: {
      type: Object,
      default: null
    }

  }

}

</script>

<style scoped>

.music-layout {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 30px;
}

/* PLAYLIST */

.playlist,
.now-playing {
  background: #191923;
  padding: 30px;
  border-radius: 20px;
  border: 1px solid #292938;
}

.section-heading {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 25px;
}

.small-title {
  color: #a78bfa;
  font-size: 11px;
  letter-spacing: 3px;
  font-weight: bold;
}

.section-heading h2 {
  color: white;
  font-size: 26px;
  margin: 8px 0;
}

.song-count {
  color: #aaa;
  font-size: 13px;
}

/* SONG CARDS */

.song-item {
  display: flex;
  align-items: center;
  padding: 13px;
  margin-bottom: 12px;
  background: #22222f;
  border-radius: 13px;
  cursor: pointer;
  transition: 0.3s;
}

.song-item:hover {
  background: #343044;
  transform: translateX(5px);
}

.song-item.active {
  background: #352c50;
  border: 1px solid #9270ee;
}

.song-image {
  width: 60px;
  height: 60px;
  object-fit: cover;
  border-radius: 10px;
}

.song-details {
  flex: 1;
  margin-left: 15px;
}

.song-details h3 {
  color: white;
  font-size: 15px;
  margin: 0 0 7px;
}

.song-details p {
  color: #999;
  font-size: 13px;
  margin: 0;
}

.play-button {
  color: #a78bfa;
  font-size: 19px;
}

/* NOW PLAYING */

.now-playing {
  text-align: center;
}

.playing-content {
  padding-top: 15px;
}

.album-cover {
  width: 230px;
  height: 230px;
  object-fit: cover;
  border-radius: 20px;
  box-shadow: 0 15px 40px rgba(0,0,0,0.4);
}

.playing-content h2 {
  color: white;
  font-size: 25px;
  margin: 25px 0 8px;
}

.artist-name {
  color: #aaa;
  font-size: 15px;
}

/* MUSIC VISUALIZER */

.music-bar {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 5px;
  height: 35px;
  margin: 25px 0;
}

.music-bar span {
  width: 5px;
  height: 15px;
  background: #a78bfa;
  border-radius: 5px;
}

.music-bar span:nth-child(2),
.music-bar span:nth-child(6) {
  height: 30px;
}

.music-bar span:nth-child(3),
.music-bar span:nth-child(8) {
  height: 22px;
}

.music-bar span:nth-child(4) {
  height: 35px;
}

.control-buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 35px;
  color: white;
  font-size: 23px;
}

.main-play {
  background: #8b5cf6;
  width: 55px;
  height: 55px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
}

.status {
  color: #a78bfa;
  font-size: 10px;
  letter-spacing: 3px;
  margin-top: 30px;
}

/* EMPTY STATE */

.empty-state {
  padding: 65px 15px;
}

.empty-icon {
  width: 85px;
  height: 85px;
  margin: auto;
  background: #29233c;
  color: #a78bfa;
  font-size: 50px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.empty-state h2 {
  color: white;
  margin-top: 25px;
}

.empty-state p {
  color: #999;
  line-height: 1.8;
  font-size: 14px;
}

/* MOBILE */

@media (max-width: 750px) {

  .music-layout {
    grid-template-columns: 1fr;
  }

  .playlist,
  .now-playing {
    padding: 20px;
  }

  .album-cover {
    width: 190px;
    height: 190px;
  }

}

</style>
