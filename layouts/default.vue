<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
    >
      <v-list dense>
        <nuxt-link to="/">
          <v-list-item @click="">
            <v-list-item-action>
              <v-icon>mdi-home</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>
                Home
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </nuxt-link>
        <nuxt-link to="/about">
          <v-list-item @click="">
            <v-list-item-action>
              <v-icon>face</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>
                About
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </nuxt-link>
        <nuxt-link to="/">
          <v-list-item @click="">
            <v-list-item-action>
              <v-icon>contact_support</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>
                Contact
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </nuxt-link>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      color="primary"
      fixed
      app
      clipped-left
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <nuxt-link to="/">
        <v-toolbar-title class="text-uppercase white--text">
          <span class="font-weight-light">Pies by</span>
          <span>Naan</span>
        </v-toolbar-title>
      </nuxt-link>
      <v-spacer></v-spacer>
      <nuxt-link to="/">
        <v-icon
          medium
          class="mr-2"
        >
          language
        </v-icon>
      </nuxt-link>
    </v-app-bar>
    <v-content>
      <v-container class="fill-height"
                   fluid>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer
      color="primary"
      app
    >
      <span>&copy; Pies by Naan</span>
      <v-spacer></v-spacer>
      <v-icon>
        chat
      </v-icon>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: true,
    }
  }
}
</script>

<style>
  .v-application a {
    text-decoration: none;
    color: inherit;
  }
</style>
