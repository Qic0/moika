<template>
  <v-app>
    <v-navigation-drawer
      app
      temporary
      v-model="drawer">
      <h1> тут пока пусто</h1>
<!--            <v-list>-->
<!--              <v-list-tile-->
<!--                      v-for="link of links"-->
<!--                      :key="link.title"-->
<!--                      :to="link.url"-->
<!--              >-->
<!--                <v-list-tile-action>-->
<!--                  <v-icon>{{link.icon}}</v-icon>-->
<!--                </v-list-tile-action>-->
<!--                <v-list-tile-content>-->
<!--                  <v-list-tile-title v-text="link.title"></v-list-tile-title>-->
<!--                </v-list-tile-content>-->
<!--              </v-list-tile>-->
<!--            </v-list>-->
    </v-navigation-drawer>

    <v-toolbar app dark color="black">
      <v-toolbar-side-icon
        @click="drawer = !drawer"
      ></v-toolbar-side-icon>

      <v-toolbar-title>
        <router-link to="/" tag="span" class="pointer">
          Мойки для моек
        </router-link>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn
          v-for="link in links"
          :key="link.title"
          :to="link.url"
          flat
        >
          <v-icon left>{{link.icon}}</v-icon>
          {{link.title}}
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>

    <v-content>

      <router-view></router-view>
    </v-content>
    <span>by qic0
        <v-icon color="black">accessible_forward
        </v-icon>
      </span>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: false,
        links: [
          {title: 'Вход', icon: 'lock', url: '/login'},
          {title: 'Регестрация', icon:'account_circle', url: '/reg'}
      ]
    }
  }
}
</script>


<style scoped>
  .pointer{
    cursor: pointer;
  }
</style>
