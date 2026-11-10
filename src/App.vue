<template>

  <div class="app-container">


<!-- HEADER -->

<header class="header">

  <div class="logo">
    <span class="logo-icon">♫</span>
    <span>Mp3<span class="highlight">Play</span></span>
  </div>

  <div class="header-text">
    <p>YOUR PERSONAL MUSIC SPACE</p>
    <h1>Feel Every <span>Beat.</span></h1>
    <p class="subtitle">
      Discover your sound. Enjoy your moment.
    </p>
  </div>

</header>


<!-- MAIN CONTENT -->

<main class="main-content">

  <div class="welcome-section">
    <div>
      <p class="welcome-label">WELCOME BACK</p>
      <h2>Music Library</h2>
    </div>

    <div class="library-badge">
      ♫ {{ songs.length }} Tracks
    </div>
  </div>


  <!-- SONG COMPONENT -->

  <SongDisplay
    :songs="songs"
    :currentSong="currentSong"
    @select-song="playSong"
  />

</main>


<!-- FOOTER -->

<footer>
  <p>Mp3Play © 2026 | MADE FOR MUSIC LOVERS</p>
</footer>


  </div>

</template>

<script>

import SongDisplay from './components/SongDisplay.vue'

export default {

  name: 'App',

  components: {
    SongDisplay
  },

  data() {

    return {

      currentSong: null,

      songs: [

        {
          title: "Blinding Lights",
          artist: "The Weeknd",
          song_id: 1,
          image_url: "https://images.unsplash.com/photo-1470225620780-dba8ba36b745?w=500"
        },

        {
          title: "Perfect",
          artist: "Ed Sheeran",
          song_id: 2,
          image_url: "https://images.unsplash.com/photo-1516280440614-37939bbacd81?w=500"
        },

        {
          title: "Levitating",
          artist: "Dua Lipa",
          song_id: 3,
          image_url: "https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?w=500"
        },

        {
          title: "Stay",
          artist: "The Kid LAROI",
          song_id: 4,
          image_url: "https://images.unsplash.com/photo-1506157786151-b8491531f063?w=500"
        },

        {
          title: "Shape of You",
          artist: "Ed Sheeran",
          song_id: 5,
          image_url: "https://images.unsplash.com/photo-1514525253161-7a46d19cd819?w=500"
        },

        {
          title: "Starboy",
          artist: "The Weeknd",
          song_id: 6,
          image_url: "https://images.unsplash.com/photo-1516280440614-37939bbacd81?w=500"
        }

      ]

    }

  },

  methods: {

    playSong(song) {

      this.currentSong = song

    }

  }

}

</script>

<style>

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
  background: #101018;
}

.app-container {
  min-height: 100vh;
  color: white;
}

/* HEADER */

.header {
  background: linear-gradient(135deg, #21163c, #171322);
  padding: 30px 8%;
  border-bottom: 1px solid #302744;
}

.logo {
  font-size: 22px;
  font-weight: bold;
  letter-spacing: 2px;
}

.logo-icon {
  color: #a78bfa;
  font-size: 28px;
  margin-right: 8px;
}

.highlight {
  color: #a78bfa;
}

.header-text {
  text-align: center;
  padding: 45px 10px 30px;
}

.header-text > p:first-child {
  color: #a78bfa;
  letter-spacing: 4px;
  font-size: 11px;
}

.header-text h1 {
  font-size: 52px;
  margin: 15px 0;
}

.header-text h1 span {
  color: #a78bfa;
}

.subtitle {
  color: #aaa;
  font-size: 15px;
}

/* MAIN */

.main-content {
  max-width: 1150px;
  margin: auto;
  padding: 45px 25px;
}

.welcome-section {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 25px;
}

.welcome-label {
  color: #a78bfa;
  font-size: 11px;
  letter-spacing: 3px;
}

.welcome-section h2 {
  font-size: 27px;
  margin: 8px 0 25px;
}

.library-badge {
  background: #29233c;
  color: #c4b5fd;
  padding: 12px 20px;
  border-radius: 30px;
  font-size: 13px;
}

/* FOOTER */

footer {
  text-align: center;
  padding: 30px 15px;
  color: #777;
  font-size: 11px;
  letter-spacing: 2px;
  border-top: 1px solid #29233c;
}

@media (max-width: 600px) {

  .header-text h1 {
    font-size: 36px;
  }

  .welcome-section {
    align-items: flex-start;
  }

}

</style>
