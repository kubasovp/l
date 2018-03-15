<template>
  <v-content>
    <section>
      <v-toolbar color="blue" dark>
        <div class="display-1">Расписание занятий</div>
      </v-toolbar>
      <v-container fluid grid-list-md class="grey lighten-4">
        <v-layout row wrap>
          <v-flex xs12 sm4
            v-for="day in days"
            :key="day.title"
          >
            <v-card>
              <v-card-media
                class="blue"
              >
                <v-container class="pa-2" fill-height fluid>
                  <v-layout fill-height>
                    <v-flex xs12 align-end flexbox>
                      <span class="headline white--text" v-text="day.title"></span>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-card-media>
              <v-card-title primary-title>
                <table class="datatable table">
                  <thead>
                    <tr>
                      <th class="text-xs-left">Время</th>
                      <th class="text-xs-left">Группа</th>
                      <th class="text-xs-left">Уровень</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                      <td v-if="day.rstatus">{{ day.rstatus }}</td>
                      <td v-if="day.rtime0">{{ day.rtime0 }}</td>
                      <td v-if="day.rgroup0">{{ day.rgroup0 }}</td>
                      <td v-if="day.rlvl0">{{ day.rlvl0 }}</td>
                    </tr>
                    <tr>
                      <td v-if="day.rtime1">{{ day.rtime1 }}</td>
                      <td v-if="day.rgroup1">{{ day.rgroup1 }}</td>
                      <td v-if="day.rlvl1 ">{{ day.rlvl1 }}</td>
                    </tr>
                    <tr>
                      <td v-if="day.rtime2">{{ day.rtime2 }}</td>
                      <td v-if="day.rgroup2">{{ day.rgroup2 }}</td>
                      <td v-if="day.rlvl2 ">{{ day.rlvl2 }}</td>
                    </tr>
                  </tbody>
                </table>

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
      days: [
        { title: 'Понедельник',
          rtime0: '17:30–18:50',
          rtime1: '19:00–20:20',
          rtime2: '20:30–21:50',
          rgroup0: '1B',
          rgroup1: '2E',
          rgroup2: '3P',
          rlvl0: 'Beginner',
          rlvl1: 'Elementary',
          rlvl2: 'Pre-intermediate'
        },
        { title: 'Вторник',
          rtime0: '17:10–18:30',
          rtime1: '18:40–20:00',
          rtime2: '20:10–21:30',
          rgroup0: '4E',
          rgroup1: '5B',
          rgroup2: '6E',
          rlvl0: 'Elementary',
          rlvl1: 'Beginner',
          rlvl2: 'Elementary'
        },
        { title: 'Среда',
          rtime0: '17:30–18:50',
          rtime1: '19:00–20:20',
          rtime2: '20:30–21:50',
          rgroup0: '1B',
          rgroup1: '2E',
          rgroup2: '3P',
          rlvl0: 'Beginner',
          rlvl1: 'Elementary',
          rlvl2: 'Pre-intermediate'
        },
        { title: 'Четверг',
          rtime0: '17:10–18:30',
          rtime1: '18:40–20:00',
          rtime2: '20:10–21:30',
          rgroup0: '4E',
          rgroup1: '5B',
          rgroup2: '6E',
          rlvl0: 'Elementary',
          rlvl1: 'Beginner',
          rlvl2: 'Elementary'
        },
        { title: 'Пятница, суббота',
          rstatus: 'Выходной!'
        },
        { title: 'Воскресенье — занятия онлайн',
          rtime0: '13:00–15:00',
          rtime1: '15:20–16:40',
          rtime2: '10:00–20:00',
          rgroup0: '4I',
          rgroup1: 'G1',
          rgroup2: 'T',
          rlvl0: 'Intermediate',
          rlvl1: 'Грамматика',
          rlvl2: 'Тестирование (запись по телефону)'
        }
      ]
    })
  }
</script>