<template>
    <div class="top-tracks sc-flex-center flex-col gap-10">
        <h1 class="top-title">✽ Top Tracks ✽</h1>

        <div class="sc-flex-center flex-wrap gap-10">
            <SongCard v-for="track in topAll?.tracks" :key="track.name" :track="track" />
        </div>
    </div>

    <div class="top-artists sc-flex-center flex-col gap-10">
        <h1 class="top-title">✽ Top Artists ✽</h1>

        <div class="sc-flex-center flex-wrap gap-10">
            <SongCard v-for="artist in topAll?.artists" :key="artist.name" :artist="artist" />
        </div>
    </div>
</template>

<script setup lang="ts">
import { useSpotifyStore } from '@/stores/spotify'
import { TopAll } from '@/libs/spotify'

const spotifyStore = useSpotifyStore()
const topAll = ref<TopAll | null>(null)

try {
    topAll.value = await spotifyStore.getTopAll()
} catch (error) {
    console.error(error)
}
</script>

<style scoped>
/* Warna untuk judul */
.top-title {
  font-family: 'KATSUMI', sans-serif ;
  margin: 0;
  font-size: 1.875rem;
  letter-spacing: 0.05em;
  color: #3d3b3c;
}

.dark .top-title {
  color: #c9c8c7;
}
</style>
