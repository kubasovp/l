<template>
  <v-content>
    <section>
      <v-toolbar color="blue" dark>
        <div class="display-1">Отзывы</div>
      </v-toolbar>
      <v-container grid-list-md text-xs-center>
        <v-layout row wrap>
          <v-flex xs12 sm6>
            <v-card color="primary">
              <v-list three-line>
                <template v-for="item in items">
                  <v-divider class="mb-2" v-if="item.divider" v-bind:inset="item.inset"></v-divider>
                  <v-list-tile avatar v-else v-bind:key="item.title">
                    <v-list-tile-avatar>
                      <img v-bind:src="item.avatar"/>
                    </v-list-tile-avatar>
                    <v-list-tile-content>
                      <v-list-tile-title v-html="item.title"></v-list-tile-title>
                      <v-list-tile-sub-title class="pb-2 grey--text text--darken-4" v-html="item.subtitle"></v-list-tile-sub-title>
                    </v-list-tile-content>
                  </v-list-tile>
                </template>
              </v-list>
            </v-card>
          </v-flex>
          <v-flex xs6>
            <v-card>
              <v-card-text class="px-0">
                <v-container>
                  <v-layout wrap>
                    <v-flex>
                      <v-form v-model="valid" ref="form" lazy-validation>
                        <v-text-field
                          label="Имя"
                          v-model="name"
                          :counter="10"
                          required
                        ></v-text-field>
                        <v-text-field
                          label="E-mail"
                          v-model="email"
                          required
                        ></v-text-field>
                        <v-text-field
                          label="Ваш отзыв"
                          v-model="mess"
                          multi-line
                        ></v-text-field>
                        <v-btn @click="submit">submit</v-btn>
                        <v-btn @click="clear">clear</v-btn>
                      </v-form>
                  </v-flex>
                  </v-layout>
                </v-container>
              </v-card-text>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </section>
  </v-content>
</template>

<script>
  import axios from 'axios'

  export default {
    data: () => ({
      items: [
        {
          avatar: '/img/feedback/1.jpg',
          title: 'Name',
          subtitle: 'Отходила месяц. Педагог хороший. Объясняет доходчиво. Удобное расположение. 3 мин. от метро. Всем рекомендую.'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/2.jpg',
          title: 'Name',
          subtitle: 'Отличная , оригинальная методика обучения))) уютная атмосфера))замечательный преподаватель )) на уроках чувствуешь себя ,как дома )))'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/3.jpg',
          title: 'Name',
          subtitle: 'Я много раз начинала учить английский язык и каждый раз все мои начинания заканчивались ничем. Да еще и с преподавателем очень повезло: Ольга. Занятия пролетают как один миг, настолько они интересны. И усваивается все очень хорошо. Я очень довольна,так как и грамматика продвигается и словарный запас увеличивается. Благодарю Ольгу за интересные занятия и уютную обстановку.'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/4.jpg',
          title: 'Name',
          subtitle: 'Замечательная атмосфера изучения английского. Можно прямо на уроке заварить чай или съесть пару-тройку вкусных конфет, при этом не отвлекаясь от общего дела Не может не радовать пешая доступность от метро. Ольга очень добродушный и отзывчивый преподаватель. К каждому найдёт подход и всегда рада помочь при возникновении каких либо трудностей с изучением английского.'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/5.jpg',
          title: 'Name',
          subtitle: 'Добрый день. Для меня вчера был первый день занятий. Ольга (преподаватель), потрясающая девушка и доходчиво всё объясняет,приободряет и всячески создает уютную обстановку для учёбы. Успех зависит только от кропотливых усилий над собой,но уверена,что всё осуществлю и прекращу бояться говорить (: Так что не жалейте ни времени,ни денег...Оно того стоит. Вы только начните,а дальше все станет получаться (: Спасибо за такие возможности.'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/6.jpg',
          title: 'Алена',
          subtitle: 'Спасибо Вам! Все так классно и материалы и сам курс!) Я конечно была в шоке от объема материалов,) но получив результат я с уверенностью могу сказать что мне все это понравилось, и я реально все успевала. В начале я сомневалась во всем этом и в себе… но вдруг поняла что в душе всю жизнь) хотела такую систему обучения)… все сразу и за короткий сроки так систематично!!!'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/7.jpg',
          title: 'Екатерина',
          subtitle: 'Нас очень очаровали Вы и ваша методика преподавания. Мы желаем Вам удачи и огромного развития и никогда не останавливаться на достигнутом. Вы стали нам родным человеком. Я никогда не учившая язык, сейчас общаюсь на работе с американцами и по телефону и они меня понимают!'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/8.jpg',
          title: 'Вера',
          subtitle: 'This course is special course so I like it. First of all it really helps me to learn English. But this is not all. The course disciplined me, made me feel positive. Now I can do a lot of business and I am seldom tired. So I think about my dreams more because now I know that everything is possible. Thanks Olga.'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/9.jpg',
          title: 'Анатолий',
          subtitle: 'This course gave us a real chance to learn English. It helped us to believe in our mental power. I was interested in learning English in a short time. Today the knowledge of the language is the most important. Thanks for our wonderful teacher!'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/10.jpg',
          title: 'Татьяна',
          subtitle: 'Спасибо за замечательный курс в рамках данной программы «Скажи барьеру - нет». Ваш позитивный настрой, оптимизм и уверенность в том, что мы сможем выучить английский, системность и последовательность в материале, жесткие требования, разбавленные светлым юмором – это то, что необходимо сомневающимся, но желающим выучить язык взрослым.'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/11.jpg',
          title: 'Виталий',
          subtitle: 'Большое спасибо нашему преподавателю – Ольге Валерьевне, за ее терпение, положительную энергию и реальное желание передать нам свои знания. Благодаря Вам, хочется продолжать изучать язык.'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/12.jpg',
          title: 'Ирина Яронтовская',
          subtitle: 'I like this course because I wanted to learn English in a short time. I like Olga because she is a creative and positive teacher. I became more organized. I am sure I will be more successful after this course.'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/13.jpg',
          title: 'Настя Герасимова',
          subtitle: 'Я занималась на курсах Ольги, могу сказать, что у нее правильная методика обучения, я подняла свой уровень английского с уровня elementary до уровня intermediate всего за пять месяцев. Благодаря ее курсам и ее помощи я получила визу в Англию, где успешно сдала экзамен IELTS, и прошла стажировку за границей. Благодаря ее методике обучения у меня появился настоящий интерес в изучении английского языка, как говорится «почувствовала и прониклась языком». Если вы планируете изучать английский, данные курсы вам помогут. Проверено на собственном опыте!!!!! Не пожалеете.'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/14.jpg',
          title: 'Айжан',
          subtitle: 'Мне очень понравилось как ведет урок Ксения. Она хорошо ведет урок, активно, бодренько, произношение хорошее, хорошо преподносит материал. Всем уделяет внимание. Старается говорить и объяснять только на английском, не забывая при этом и про русский. Молодая, приятная, активная. Старается по максимуму использовать выделенное на урок время. Нацелена на результат. Ксения молодец)) Желаю ей успехов.))'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/15.jpg',
          title: 'Ольга',
          subtitle: 'Хочу выразить благодарность и поздравить своего учителя Ольгу, с наступившими праздниками!!!! Пожелать дальнейшего развития вам (и себе в освоении языка). Редко встретишь преподавателя более внимательного и терпеливого. Спасибо!!!'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/16.jpg',
          title: 'Зоя',
          subtitle: 'Несколько занятий с Ольгой по грамматике позволили уложить в голове стройными рядами все те знания, которые получала годами, но не могла использовать. Еще раз спасибо Ольге и всем, кто помогает ей в организации школы. Обязательно рекомендую всем своим друзьям, знакомым и всем остальным, кто хочет расширить границы своего образования и нашего мира: кто еще не присоединился к школе ReachGoal, ПРИСОЕДИНЯЙТЕСЬ!!!! Вы не будете разочарованы!'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/17.jpg',
          title: 'Виктория',
          subtitle: 'Хочу выразить слова огромной благодарности Оле!! Это не первая моя попытка выучить английский язык. Но только в этой школе на этих вебинарах в моей голове все наконец-то разложилось по полочкам. Конечно, многое зависит от меня самой, но здесь такая мощная мотивация и коллективный дух, что не учить и не выучить не возможно. Отдельное спасибо Ксении, Джулии и Рафаэлю!!! Ура!!!'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/15.jpg',
          title: 'Ольга',
          subtitle: 'Хочу выразить благодарность и поздравить своего учителя Ольгу, с наступившими праздниками!!!! Пожелать дальнейшего развития вам (и себе в освоении языка). Редко встретишь преподавателя более внимательного и терпеливого. Спасибо!!!'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/16.jpg',
          title: 'Зоя',
          subtitle: 'Несколько занятий с Ольгой по грамматике позволили уложить в голове стройными рядами все те знания, которые получала годами, но не могла использовать. Еще раз спасибо Ольге и всем, кто помогает ей в организации школы. Обязательно рекомендую всем своим друзьям, знакомым и всем остальным, кто хочет расширить границы своего образования и нашего мира: кто еще не присоединился к школе ReachGoal, ПРИСОЕДИНЯЙТЕСЬ!!!! Вы не будете разочарованы!'
        },
        { divider: true, inset: true },
        {
          avatar: '/img/feedback/17.jpg',
          title: 'Виктория',
          subtitle: 'Хочу выразить слова огромной благодарности Оле!! Это не первая моя попытка выучить английский язык. Но только в этой школе на этих вебинарах в моей голове все наконец-то разложилось по полочкам. Конечно, многое зависит от меня самой, но здесь такая мощная мотивация и коллективный дух, что не учить и не выучить не возможно. Отдельное спасибо Ксении, Джулии и Рафаэлю!!! Ура!!!'
        }
      ],
      valid: true,
      name: '',
      nameRules: [
        (v) => !!v || 'Name is required',
        (v) => (v && v.length <= 10) || 'Name must be less than 10 characters'
      ],
      email: '',
      emailRules: [
        (v) => !!v || 'E-mail is required',
        (v) => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
      ],
      mess: ''
    }),
    methods: {
      submit () {
        if (this.$refs.form.validate()) {
          // Native form submission is not yet supported
          axios.post('/api/submit', {
            name: this.name,
            email: this.email,
            mess: this.mess
          })
        }
      },
      clear () {
        this.$refs.form.reset()
      }
    }
  }
</script>

<style>
  .list--three-line .list__tile {
    height: auto;
  }
  .list--three-line .list__tile__sub-title {
    -webkit-line-clamp: inherit;
  }
  .list__tile {
    align-items: start;
  }
</style>
