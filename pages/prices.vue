<template>
  <v-content>
    <section>
      <v-toolbar color="blue" dark>
        <div class="display-1">Цены</div>
      </v-toolbar>
      <v-container fluid grid-list-md class="grey lighten-4">
        <v-layout row wrap>
          <v-flex xs12 sm6
            v-for="card in cards"
            :key="card.title"
          >
            <v-card>
              <v-card-media
                class="blue"
              >
                <v-container class="pa-2" fill-height fluid>
                  <v-layout fill-height>
                    <v-flex xs12 align-end flexbox>
                      <span class="headline white--text" v-text="card.title"></span>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-card-media>
              <v-card-title primary-title>
                <ul class="pb-3 pl-3">
                  <li>Уровень: {{ card.plvl }}</li>
                  <li v-if="card.pgroup">Человек в группе: {{ card.pgroup }}</li>
                  <li>Длительность урока: {{ card.plestime }}</li>
                  <li>Уроков в месяц: {{ card.plesmonth }}</li>
                  <li v-if="card.plength">Длительность курса: {{ card.plength }}</li>
                  <li>Стоимость за месяц: {{ card.price }}</li>
                  <li>Скидка при оплате за курс: {{ card.discount }}</li>
                </ul>
              </v-card-title>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </section>
  </v-content>
</template>

<script>
  export default {
    data: () => ({
      cards: [
        { title: 'Общая программа',
          plvl: 'от начального до продвинутого',
          pgroup: 'до 10',
          plestime: '80 минут',
          plesmonth: '8',
          plength: '8 месяцев',
          price: '4 800 рублей',
          discount: ''
        },
        { title: 'Корпоративная программа ',
          plvl: 'от начального до продвинутого',
          pgroup: 'до 10',
          plestime: '80 минут',
          plesmonth: '8',
          plength: '8 месяцев',
          price: '21 000 рублей за группу',
          discount: ''
        },
        { title: 'Индивидуальная программа',
          plvl: 'от начального до продвинутого',
          pgroup: '1',
          plestime: 'от 80 минут',
          plesmonth: '8',
          plength: '8 месяцев',
          price: '750 рублей ак. час',
          discount: ''
        },
        { title: 'Грамматика (онлайн)',
          plvl: 'от начального до продвинутого',
          pgroup: '',
          plestime: '80 минут',
          plesmonth: '4',
          plength: '',
          price: '1 200 рублей',
          discount: ''
        }
      ]
    })
  }
</script>