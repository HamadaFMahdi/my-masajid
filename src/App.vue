<template>
  <v-app>
    <GmapMap
      :center="{lat:51.5074, lng:0.1278}"
      :zoom="11"
      map-type-id="terrain"
      style="width: 100%; height: 100%"
    >
      <GmapCluster :gridSize="50">
        <GmapMarker
          v-for="(p, i) in places"
          :index="i"
          :key="i"
          :position="{lat:p.FIELD2, lng:p.FIELD1}"
          :clickable="true"
          :draggable="false"
        />
      </GmapCluster>
    </GmapMap>
  </v-app>
</template>

<script>
import { data } from "../data.js"
import GmapCluster from 'vue2-google-maps/dist/components/cluster' // replace src with dist if you have Babel issues
export default {
  name: 'App',
  data () {
    return {
      places: data
    }
  },
  components: {
    GmapCluster
  },
  methods: {
    hello() {
      this.$refs.map.panTo({lat: 1.38, lng: 103.80})
    }
  }
}
</script>
