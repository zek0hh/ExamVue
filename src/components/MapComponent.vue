<template>
  <b-container>
    <h2 id="carte">C'est la carte !</h2>
    <div style="width: 100%"><iframe width="100%" height="600" src="https://maps.google.com/maps?width=100%&amp;height=600&amp;hl=en&amp;q=paris+(C'est%20la%20carte%20!)&amp;ie=UTF8&amp;t=&amp;z=12&amp;iwloc=B&amp;output=embed" frameborder="0" scrolling="no" marginheight="0" marginwidth="0"><a href="https://www.maps.ie/coordinates.html">latitude longitude finder</a></iframe></div><br />
  </b-container>
</template>

<script>
export default {
  name: 'MapComponent',
  data() {
    return {
      markers: [],
      infoWindow: {
        position: { lat: 0, lng: 0 },
        open: false,
        template: '',
      },
    };
  },

  methods: {
    openInfoWindowTemplate(item) {
      this.infoWindow.template = item.name;
      this.infoWindow.position = item.geometry.location;
      this.infoWindow.open = true;
    },
  },

  mounted() {
    // At this point, the child GmapMap has been mounted, but
    // its map has not been initialized.
    // Therefore we need to write mapRef.$mapPromise.then(() => ...)

    this.$refs.mapRef.$mapPromise.then((map) => {
      map.panTo({ lat: 48.864716, lng: 2.349014 });
      /* eslint-disable */
      let request = {
        location: {lat: 48.864716, lng: 2.349014},
        radius:1000,
        name:"restaurant"
      }
      let placesService = new google.maps.places.PlacesService(map)
      placesService.nearbySearch(request, (results, status) => {
          this.markers = results
          console.log(status)
        }
      )
    })
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<!--
<style scoped>

</style>
-->
