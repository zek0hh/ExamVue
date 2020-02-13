<template>
  <div id="app">
    <NavComponent/>
    <VideoContainer/>
    <b-container>
      <b-row>
        <b-col>
          <p class="leTexte"> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt
            ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation
            ullamco
            laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit
            in
            voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
            cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
          </p>
        </b-col>
        <b-col>
          <p class="leTexte"> Lorem ipsum dolor sit amet, consectetur adipiscing elit,
            sed do eiusmod tempor incididunt
            ut labore et dolore magna aliqua.
            Ut enim ad minim veniam, quis nostrud exercitation ullamco
            laboris nisi ut aliquip
            voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
            cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
          </p>
        </b-col>
      </b-row>
    </b-container>
    <MapComponent/>
    <b-container>
        <b-form-group
          id="fieldset-1"
          description="Laissez nous votre nom"
          label="Le bloc d'inscription"
          label-for="input-1"
          :invalid-feedback="invalidFeedback"
          :valid-feedback="validFeedback"
          :state="state"
        >
          <b-form-input id="input-1" v-model="name" :state="state" trim></b-form-input>
        </b-form-group>
    </b-container>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.leTexte {
  padding: 10px;
}
</style>
<script>
// eslint-disable-next-line import/extensions
import NavComponent from '@/components/NavComponent';
import VideoContainer from '@/components/VideoContainer.vue';
import MapComponent from '@/components/MapComponent.vue';

export default {
  computed: {
    state() {
      return this.name.length >= 4;
    },
    invalidFeedback() {
      if (this.name.length > 4) {
        return '';
      } if (this.name.length > 0) {
        return 'Entrez au moins 4 caractères';
      }
      return 'Faudrait taper quelque chose';
    },
    validFeedback() {
      return this.state === true ? 'Merci :)' : '';
    },
  },
  data() {
    return {
      name: '',
    };
  },
  components: { MapComponent, VideoContainer, NavComponent },
};
</script>
