<template>
  <v-app light>
    <v-navigation-drawer
      :mini-variant="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      fixed
      app
    >
      <div class="layout pt-3 justify-center wrap">
        <div class="your-logo-here card card--flat theme--light" style="height:auto;" data-ripple="false">
          <div class="card__text">
            <div class="layout justify-center">
              <div class="flex text-xs-center">
                <div class="body-2 mb-4">
                  Diamond Sponsors
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <v-list>
        <v-list-tile 
          router
          :to="item.to"
          :key="i"
          v-for="(item, i) in items"
          exact
          ripple
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

          <v-dialog v-model="dialog" max-width="500px">
            <v-btn class="grey lighten-4 blue--text text--accent-4" dark slot="activator">Заказать звонок</v-btn>
            <v-card>
              <v-card-text>
                <v-container grid-list-md>
                  <v-layout wrap>

                    <v-form v-model="valid" ref="form" lazy-validation>
                      <v-text-field
                        label="Имя"
                        v-model="name"
                        :rules="nameRules"
                        required
                      ></v-text-field>
                      <v-text-field
                        label="Телефон"
                        v-model="number"
                        :rules="numberRules"
                        required
                      ></v-text-field>
                      <v-btn
                        @click="submit"
                        :disabled="!valid"
                      >
                        Отправить
                      </v-btn>
                      <v-btn @click="clear">Очистить</v-btn>
                    </v-form>

                  </v-layout>
                </v-container>
              <small>*indicates required field</small>
              </v-card-text>
            </v-card>
          </v-dialog>

    </v-toolbar>
    <main>
      <nuxt />
    </main>
    <v-footer :fixed="fixed" app>
      <span>&copy; 2010–2017 {{ title }}</span>
    </v-footer>
  </v-app>
</template>

<script>
  import axios from 'axios'
  export default {
    data: () => ({
      clipped: false,
      drawer: true,
      fixed: false,
      items: [
        { icon: 'apps', title: 'Welcome', to: '/' },
        { icon: 'school', title: 'Школа', to: '/school' },
        { icon: 'description', title: 'Программы', to: '/programs' },
        { icon: 'monetization_on', title: 'Цены', to: '/prices' },
        { icon: 'zoom_in', title: 'Методика', to: '/methods' },
        { icon: 'list', title: 'Расписание', to: '/class-schedule' },
        { icon: 'new_releases', title: 'Анонсы', to: '/announcement' },
        { icon: 'comment', title: 'Отзывы', to: '/feedback' },
        { icon: 'account_balance', title: 'Интерьер', to: '/interior' },
        { icon: 'phone_in_talk', title: 'Контакты', to: '/contact' }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Lingology — курсы английского языка в Москве',
      dialog: false,
      valid: true,
      name: '',
      nameRules: [
        (v) => !!v || 'Имя обязательно :)'
      ],
      number: '',
      numberRules: [
        (v) => !!v || 'Телефон обязательно :)'
      ]
    }),
    methods: {
      submit () {
        if (this.$refs.form.validate()) {
          // Native form submission is not yet supported
          axios.post('/api/submit', {
            name: this.name,
            number: this.number
          })
        }
      },
      clear () {
        this.$refs.form.reset()
      }
    },
    head: {
      title: 'Школа Lingology — курсы английского языка в Москве'
    }
  }
</script>

<style>
  body {
    font-family: 'Roboto Condensed', sans-serif;
    font-size: 16px;
    line-height: 1.4;
  }
  .application {
    font-family: 'Roboto Condensed', sans-serif;
    line-height: 1.4;
  }
  .tabs__item {
    text-transform: unset;
  }
  .navigation-drawer>.list:not(.list--dense) .list__tile {
    font-family: Roboto,sans-serif;
    font-size: 16px;
  }
</style>
