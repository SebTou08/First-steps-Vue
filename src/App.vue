<template>
  <v-card
      class="mx-auto"
      max-width="344"
      outlined
  >
    <v-list-item three-line>
      <v-list-item-content>
        <div class="text-overline mb-4">
          Seguidores de @{{fullName}}
        </div>
        <v-list-item-title class="text-h5 mb-1">
          <strong>Numero oficial de seguidores:</strong>{{followers}}
        </v-list-item-title>
        <v-list-item-subtitle>En esta parte puedes aumentar los seguidores con el boton </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar
          tile
          size="80"
          color="grey"
      ></v-list-item-avatar>
    </v-list-item>

    <v-card-actions>
      <v-btn
          outlined
          rounded
          text
          v-on:click="followUser"
      >
        Seguir
      </v-btn>
      <v-spacer></v-spacer>
      <v-btn
          outlined
          rounded
          text
          v-on:click="unfollowUser"
      >
        Dejar de seguir
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>

export default {
  name: 'App',

  components: {
  },

  data: () => ({
    followers: 0,
    user: {
      id: 1,
      username: '_sebTou',
      firstName: 'sebastian',
      lastname: 'toulier',
      email: 'seb@gmail.com',
      isAdmin: true
    }
  }),

  watch: {
    followers(newFollowerCount, oldFollowerCount){
      if(oldFollowerCount< newFollowerCount){
        console.log(`${this.user.username} has gained a follower!`)
      }
    }
  },

  computed: {
    fullName(){
      return `${this.user.firstName} ${this.user.lastname}`
    }
  },

  methods: {
    followUser(){
      this.followers++;
    },
    unfollowUser(){
      if(this.followers > 0){
        this.followers--;
      }
    }
  },
  mounted() {
    this.followUser();
  }

};
</script>
