<template>
  <v-app>
    <!-- LNB -->
    <v-navigation-drawer fixed clipped app class="grey lighten-4" v-model="drawer">
      <v-list dense class="grey lighten-4">
        <template v-for="(item, i) in items">
          <v-layout row v-if="item.heading" align-center :key="i">
            <v-flex xs6>
              <v-subheader v-if="item.heading">
                {{ item.heading }}
              </v-subheader>
            </v-flex>
          </v-layout>
          <v-divider dark v-else-if="item.divider" class="my-3" :key="i"></v-divider>
          <v-list-tile :key="i" v-else @click="goMenu(item.routerName)">
            <v-list-tile-action>
              <v-icon large :color="item.color">{{ item.icon }}</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title class="grey--text">
                {{ item.text }}
              </v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </template>
      </v-list>
    </v-navigation-drawer>

    <!-- TNB -->
    <v-toolbar color="teal" app clipped-left>
      <v-toolbar-side-icon @click.native="drawer = !drawer"></v-toolbar-side-icon>
      <span class="title ml-3 mr-5">Book Repository App&nbsp;<span class="text">(v1.0.0)</span></span>
      <v-spacer></v-spacer>
      <v-btn
        flat
        :href="historyUrl"
        target="_blank"
      >
        <span class="mr-2">HISTORY</span>
      </v-btn>
    </v-toolbar>
    
    <!-- CONTENT -->
    <v-content class="grey lighten-4">
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      drawer: true,
      items: [
        { divider: true },
        { icon: 'home', text: 'Home', color: 'green', routerName : 'home' },
        { divider: true },
        { heading: 'Sample Title' },
        { icon: 'help', text: 'Sample Page', color: 'cyan', routerName: 'sample' },
        { divider: true },
      ],
      historyUrl: ''
    }
  },
  methods: {
    goMenu (routerName) {
      alert(routerName)
    }
  }
}
</script>
