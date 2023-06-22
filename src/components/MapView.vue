<template>
  <div ref="mapContainer" class="map-container"></div>
</template>

<script>
import mapboxgl from "mapbox-gl";
mapboxgl.accessToken =
  "pk.eyJ1Ijoibm92aWVhc2RmIiwiYSI6ImNsajc5b3ZiMjBkbXIzZG11dzU3YXZqNzIifQ.by0EklkMvYXoQ2yhEpVsWg";

export default {
  mounted() {
    const mapOptions = {
      container: this.$refs.mapContainer,
      style: "mapbox://styles/mapbox/streets-v12",
      center: [-74.5, 40],
      zoom: 9,
    };

    new mapboxgl.Map(mapOptions);
  },
};
</script>

<style>
.map-container {
  width: 100%;
  height: 100%;
}
</style>
