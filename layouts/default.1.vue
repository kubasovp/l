<template>
  <v-app light><!-- /////////////////////////////////////////////////// Левый сайдбар -->
    <v-navigation-drawer
      :mini-variant="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      fixed
      app
    >
      <v-list>
        <v-list-tile 
          router
          :to="item.to"
          :key="i"
          v-for="(item, i) in items"
          exact
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer><!-- ////////////////////////////////////////// Левый сайдбар -->
    <v-toolbar fixed app :clipped-left="clipped">
      <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-navigation-drawer
      temporary
      :right="right"
      v-model="rightDrawer"
      fixed
    >
      <v-list>
        <v-list-tile @click.native="right = !right">
          <v-list-tile-action>
            <v-icon light>compare_arrows</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Switch drawer (click me)</v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-footer :fixed="fixed" app>
      <span>&copy; 2017</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        clipped: false,
        drawer: true,
        fixed: false,
        items: [
          { icon: 'apps', title: 'Welcome', to: '/' },
          { icon: 'star', title: 'Анонсы', to: '/announcement' },
          { icon: 'star', title: 'Методы', to: '/methods' },
          { icon: 'star', title: 'Отзывы', to: '/feedback' },
          { icon: 'star', title: 'Контакты', to: '/contact' },
          { icon: 'star', title: 'Цены', to: '/prices' },
          { icon: 'star', title: 'Расписание', to: '/class-schedule' },
          { icon: 'star', title: 'Программы', to: '/courses' },
          { icon: 'star', title: 'Школы', to: '/school' },
          { icon: 'star', title: 'Интерьер', to: '/interior' },
          { icon: 'star', title: 'Inspire', to: '/inspire' }
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Lingology'
      }
    },
    head: {
      title: 'Школа Lingology — курсы английского языка в Москве'
    }
  }
</script>
