<template>
  <div id="map" ref="mapContainer" style="height: 600px; width: 100%;"></div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';
import L from 'leaflet';

// Import marker images
import markerIcon2x from 'leaflet/dist/images/marker-icon-2x.png';
import markerIcon from 'leaflet/dist/images/marker-icon.png';
import markerShadow from 'leaflet/dist/images/marker-shadow.png';

delete L.Icon.Default.prototype._getIconUrl;

L.Icon.Default.mergeOptions({
  iconRetinaUrl: markerIcon2x,
  iconUrl: markerIcon,
  shadowUrl: markerShadow,
});

const mapContainer = ref<HTMLElement | null>(null);

onMounted(() => {
  if (mapContainer.value) {
    const map = L.map(mapContainer.value).setView([56.1304, -106.3468], 4); // Centered on Canada

    // Add OpenStreetMap tiles
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution:
        '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
    }).addTo(map);

    // Sample marker
    const marker = L.marker([60.1087, -113.6426]).addTo(map);
    marker.bindPopup('<b>Example Gold Mine</b><br>Location in Canada.');
  }
});
</script>

<style scoped>
</style>
