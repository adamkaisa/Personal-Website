<template>
    <div class="spotify" v-if="currentlyPlaying || recentlyPlayed">
        <img
            :src="currentlyPlaying?.coverArt ?? recentlyPlayed?.coverArt ?? ''"
            :alt="currentlyPlaying?.name ?? recentlyPlayed?.name ?? 'Spotify Cover Art'"
            class="spotify-cover"
        />

        <div class="spotify-info">
            <Link
                :href="link"
                :label="shortenText(currentlyPlaying?.name ?? recentlyPlayed?.name ?? '', 25)"
                class="spotify-title"
            />
            <span class="artist">
                {{ currentlyPlaying?.artist ?? recentlyPlayed?.artist ?? 'Unknown Artist' }}
            </span>
            <span class="spotify-status">
                <Music class="music-icon" />
                <span id="spotify-text">
                    {{ currentlyPlaying ? 'Currently playing on Spotify' : 'Recently Played on Spotify' }}
                </span>
            </span>
        </div>
    </div>
</template>

<script setup lang="ts">
import { useSpotifyStore } from '@/stores/spotify'

const spotifyStore = useSpotifyStore()
await spotifyStore.isLoaded()

const currentlyPlaying = computed(() => spotifyStore.currentlyPlaying)
const recentlyPlayed = computed(() => spotifyStore.recentlyPlayed)
const link = computed(() => currentlyPlaying.value?.link ?? recentlyPlayed.value?.link ?? '#')

function shortenText(text: string, maxLength: number) {
    return text.length > maxLength ? text.slice(0, maxLength) + '...' : text
}
</script>

<style scoped>
.spotify {
    position: fixed;
    bottom: 2rem;
    left: 1rem;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    flex-wrap: nowrap;
    gap: 0.75rem;
    font-family: 'Nunito', sans-serif;
    padding: 0.75rem 1rem;
    background-color: #c9c8c7;
    border-radius: 0.75rem;
    width: max-content;
}

.dark .spotify {
    background-color: #282828;
}


.spotify-cover {
    border-radius: 0.25rem;
    height: 4.5rem;
    width: 4.5rem;
}

.dark .spotify-cover {
    box-shadow: none;
}

.spotify-info {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    gap: 0.25rem;
    text-align: left;
    font-size: 0.875rem;
    color: #3d3b3c;
    line-height: 1.2;
}

.dark .spotify-info {
    color: #f2f0ef;
}

.spotify-title {
    font-size: 1.125rem;
    font-weight: 500;
    color: #3d3b3c;
    letter-spacing: -0.5px;
}

.dark .spotify-title {
    color: #f2f0ef;
}

.artist {
    font-size: 0.75rem;
    margin-bottom: 0.1rem;
    font-weight: 300;
    letter-spacing: -0.3px;
}

.spotify-status {
    display: flex;
    align-items: center;
    gap: 0.3rem;
    padding: 0.3rem;
    border-radius: 0.25rem;
    background-color: #1DB954;
}

.music-icon {
    stroke: #3d3b3c;
    width: 1rem;
    height: 1rem;
}

.dark .music-icon {
    stroke: #f2f0ef;
}

#spotify-text {
    font-size: 0.75rem;
    color: #3d3b3c;
    letter-spacing: -0.3px;
}

.dark #spotify-text {
    color: #f2f0ef;
}

@media (max-width: 768px) {
    .spotify {
        top: auto;
        bottom: 7rem;
        right: auto;
        left: auto;
    }
}

</style>
