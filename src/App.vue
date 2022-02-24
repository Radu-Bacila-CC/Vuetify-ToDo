<template>
  <v-app id="inspire">
    <v-navigation-drawer
    v-model="drawer" 
    :mobile-breakpoint="768"
    app>
      <v-img
      class="pa-4 pt-7"
      height="170"
      gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
      src="https://picsum.photos/1920/1080?random">   
      <v-avatar size="70" class="mb-2">
      <img
        src="https://i.picsum.photos/id/1005/5760/3840.jpg?hmac=2acSJCOwz9q_dKtDZdSB-OIK1HUcwBeXco_RMMTUgfY"
        alt="Radu Bacila"
      >
    </v-avatar>
    <div class="white--text text-subtitle-1 font-weight-bold">
      Radu Bacila
      </div>
    <div class="white--text text-subtitle-2">
      radu.bacila
      </div>
</v-img>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="primary"
      dark
      src="https://picsum.photos/1920/1080?random"
      prominent
      :height="$route.path === '/' ? '240' : '170'"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-container
      class="header pa-a">
        <v-row>
            <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
        </v-row>
        <v-row>
            <v-app-bar-title class="text-h4 ml-4">{{$store.state.appTitle}}</v-app-bar-title>
        </v-row>
        <v-row>
            <live-date-and-time />
        </v-row>
        <v-row v-if="$route.path=== '/'">
          <field-add-task />
        </v-row>
      </v-container>
      <v-spacer></v-spacer>

      <search />

    </v-app-bar>

    <v-main>
      <router-view></router-view>
      <snackbar />

    </v-main>
  </v-app>
</template>

<script>

  export default {
    data: () => ({ 
      drawer: null,
      items: [
          { title: 'ToDo', icon: 'mdi-format-list-checks', to: '/' },
          { title: 'About', icon: 'mdi-help-box', to: '/about'},
        ], 
    }),
    components: {
      'search': require('@/components/Tools/Search.vue').default,
      'live-date-and-time': require('@/components/Tools/LiveDateAndTime.vue').default,
      'snackbar': require('@/components/Shared/Snackbar.vue').default,
      'field-add-task': require('@/components/ToDo/FieldAddTask.vue').default,
    },
    mounted(){
      this.$store.dispatch('getTasks');
    },
  }
</script>

<style lang="sass">
  .header-container
    max-width: none !important
</style>