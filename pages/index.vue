<template>
  <v-content>
    <section>
      <v-parallax src="/img/main-first.jpg" height="600">
        <v-layout
          column
          align-center
          justify-center
          class="white--text"
        >
          <h1 class="white--text mb-2 display-1 text-xs-center">Английский язык</h1>
          <div class="subheading mb-3 text-xs-center">с National Geographic</div>

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

        </v-layout>
      </v-parallax>
    </section>

    <section>
      <v-layout
        column
        wrap
        class="my-5"
        align-center
      >
        <v-flex xs12 sm4 class="my-3">
          <div class="text-xs-center">
            <h2 class="headline">Зачем изучать английский?</h2>
            <span class="subheading">
              Что он нам дает?
            </span>
          </div>
        </v-flex>
        <v-flex xs12>
          <v-container grid-list-xl>
            <v-layout row wrap align-start>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">accessibility</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">1. Успех</div>
                  </v-card-title>
                  <v-card-text>
                    Уверенность в себе, самоуважение и признание общества. Саморазвитие, увеличение собственного потенциала — актуально в любом возрасте во все времена.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">extension</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">2. Память</div>
                  </v-card-title>
                  <v-card-text>
                    Современное общество все больше полагается на гаджеты вместо развития умственных способностей. Изучая иностранный язык, мы тренируем свой мозг, так же как мы укрепляем мышцы в спортзале.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">sentiment_very_satisfied</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">3. Хобби</div>
                  </v-card-title>
                  <v-card-text>
                    Хобби привносит в жизнь приятные моменты, наполняет ее яркими красками, открывает новые грани в серых буднях. Что может быть занимательнее изучения английского языка? Когда подпевая  иностранным исполнителям ловите себя на мысли, что уже понимаете смысл, когда надпись на футболке или свитшоте уже имеет значение — ведь вы знаете, что там написано! 
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">group_add</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">4. Друзья</div>
                  </v-card-title>
                  <v-card-text>
                    С появлением социальных сетей появилась возможность легко общаться с людьми из разных стран. Знание английского поможет обзавестись интересными знакомствами, благодаря которым неизбежно возникнут новые мысли и идеи для личностного и бизнес развития. Вы найдете единомышленников, друзей, разделяющих ваши взгляды и увлечения.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">trending_up</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline blue--text">5. Карьера</div>
                  </v-card-title>
                  <v-card-text>
                    Создание успешной карьеры подразумевает знание английского языка на уровне Intermediate. Этот уровень знаний требуется для высоких должностей уже во многих российских и практически во всех международных компаниях. Для того чтобы получить эти знания с нуля, необходимо систематично изучать английский язык два с половиной года.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">euro_symbol</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline blue--text">6. Бизнес</div>
                  </v-card-title>
                  <v-card-text>
                    У Вас уже есть свой успешный бизнес — участие в семинарах, выставках и конференциях международного уровня поможет найти своего клиента и расширить рынок предоставляемых услуг за пределами России. Знание английского языка поможет сэкономить на услугах переводчика, обеспечит легкость общения с иностранными коллегами.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">stars</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">7. Работа за рубежом</div>
                  </v-card-title>
                  <v-card-text>
                    Любая работа в сфере туризма и отдыха будет доступна, будь то авторские туры, гостиничный и отельный бизнес или организация экскурсий. Вы сможете пройти собеседование для работы на круизном лайнере и путешествовать по миру, зарабатывая при этом деньги.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">stars</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">8. Волонтёрство</div>
                  </v-card-title>
                  <v-card-text>
                    Вы получите возможность стать волонтером и помогать всемирным организациям в сохранении популяций животных в дикой природе, проводить археологические исследования, помогать людям с ограниченными возможностями. Ведь это не только добрые дела, это общение с людьми со всего земного шара. Опыт международной работы обогатит ваше резюме, поможет получить новые знакомства, реализовать свои идеи и амбиции, внести свой вклад в развитие общества и укрепления международных отношений.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">local_airport</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">9. Путешествия</div>
                  </v-card-title>
                  <v-card-text>
                    Для любителей путешествовать язык дает большую степень свободы во время посещения новой страны. Английский — международный язык, на нем разговаривают повсеместно, если даже не свободно, то базовые знания есть почти у всех. Где бы вы ни были, во Франции или Малайзии, знание английского всегда будет только плюсом: вы сможете объясниться не только при заселении в отель и заказать ланч, но и узнать от местных жителей о том, что другим туристам останется неведомым — так называемые «нетуристические маршруты», местные обычаи и заповедные места, гораздо глубже проникнете в культуру страны.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">stars</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">10. Преподавание</div>
                  </v-card-title>
                  <v-card-text>
                    Если же перспектива уехать в далекие страны и путешествовать не прельщает, вы с легкостью найдете полезное применение английскому и в России. Сможете преподавать, заниматься репетиторством, а в качестве дополнительного заработка переводить различные документы, письма, лекции, рефераты, статьи и специализированную литературу.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">local_shipping</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline blue--text">11. Иммиграция</div>
                  </v-card-title>
                  <v-card-text>
                    Хотите иммигрировать в другую страну? Создать семью с иностранцем? Какими бы знаниями в других областях Вы не обладали, Вы не сможете показать свой богатый внутренний мир, если не найдете общего языка. Общение с помощью translator будет увлекательным совсем не долго, и не поможет составить полноценный диалог даже по скайпу. Знание английского языка на разговорном уровне увеличит интерес к вашей персоне и поможет завязать долгосрочные отношения.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">favorite_border</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline blue--text">12. Отношения</div>
                  </v-card-title>
                  <v-card-text>
                    Если вы до сих пор не нашли свою половинку, задумайтесь, а вдруг она понимает только английский язык и вы просто не там ищите? Люди, мечтающие обрести свою любовь, обязательно встретятся, но для этого надо не только мечтать, но идти на встречу и пусть английский в этом поможет.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">stars</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">13. Экскурсии</div>
                  </v-card-title>
                  <v-card-text>
                    Не секрет, что русская культура, красота и богатство нашей страны тоже вызывает интерес у многих иностранцев. Умение рассказать гостям столицы правильным и приятным для слуха языком о своей родине прекрасная возможность, как для привлечения иностранных капиталов в бизнес, так и просто для заведения новых знакомств и друзей со всего мира.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">ondemand_video</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">14. Фильмы на английском</div>
                  </v-card-title>
                  <v-card-text>
                    Если вы мечтали смотреть любимые сериалы и кино без дубляжа и субтитров — у вас появится эта возможность! Смотреть научно-популярные и любые другие передачи на английском, всегда оставаясь в курсе событий и новейших технологий.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">library_books</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">15. Литература на английском</div>
                  </v-card-title>
                  <v-card-text>
                    Читать художественные книги, новостные порталы, специализированную литературу, периодические и бизнес издания в оригинале. Тогда как большая часть изданий выпускается в России с опозданием в 5-8 лет, мы не можем себе позволить оставаться в неведении и упускать возможности развития только от незнания языка. Так же у вас появится возможность публиковать и свои работы на английском.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">stars</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline text-xs-center blue--text">16. Развитие детей</div>
                  </v-card-title>
                  <v-card-text>
                    Зная английский, вы сможете передать эти навыки своим детям. Дети билингвы отличаются лучшей памятью, развитой эрудицией, имеют приятное произношение, плавную и уверенную речь, почти как у носителя языка. Изучение иностранных языков позволяет ребенку расширять кругозор во всех областях знаний, укрепляет уверенность в себе и порождает страсть к учебе, так как изучение происходит легко и интуитивно, принося наибольшее удовлетворение от процесса. Многолетняя практика показывает, что дети, изучавшие иностранный язык с раннего детства, получают гораздо более высокие баллы и по другим дисциплинам.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">school</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline blue--text">17. Подготовка к ВУЗу</div>
                  </v-card-title>
                  <v-card-text>—
                    15 лет, это тот самый возраст, когда индивидуальные особенности человека начинают раскрывать свой потенциал. Перед юным поколением встает выбор своей будущей профессии, наступает пора особенно усердной подготовки к сдаче школьных и вступительных экзаменов. Конкурсная основа с каждым годом все более ужесточается, абитуриенту со знанием дополнительного языка с большей вероятностью отдадут предпочтение, ведь это весомый фактор. Важно и то, что знание английского открывает возможность поступать в иностранные ВУЗы.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 md4>
                <v-card class="elevation-0 transparent">
                  <v-card-text class="text-xs-center">
                    <v-icon x-large class="blue--text text--lighten-2">stars</v-icon>
                  </v-card-text>
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline blue--text">18. Школьникам и студентам</div>
                  </v-card-title>
                  <v-card-text>
                    Ученики, отставшие от школьной или университетской программы, с лихвой восполнят свои знания и получат уверенность в себе и своих силах, что отразится на успеваемости и по стандартным дисциплинам.
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-container>
        </v-flex>
      </v-layout>
    </section>

    <section>
      <v-parallax src="/img/main-second.jpg" height="380">
        <v-layout column align-center justify-center>
          <div class="headline white--text mb-3 text-xs-center">Web development has never been easier</div>
          <em>Kick-start your application today</em>
          <v-btn
            class="blue lighten-2 mt-5"
            dark
            large
            href="/pre-made-themes"
          >
            Get Started
          </v-btn>
        </v-layout>
      </v-parallax>
    </section>

    <section>
      <v-container grid-list-xl>
        <v-layout row wrap justify-center class="my-5">
          <v-flex xs12 sm4>
            <v-card class="elevation-0 transparent">
              <v-card-title primary-title class="layout justify-center">
                <div class="headline">Company info</div>
              </v-card-title>
              <v-card-text>
                Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare. 
                Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. 
                Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti. 
              </v-card-text>
            </v-card>
          </v-flex>
          <v-flex xs12 sm4 offset-sm1>
            <v-card class="elevation-0 transparent">
              <v-card-title primary-title class="layout justify-center">
                <div class="headline">Contact us</div>
              </v-card-title>
              <v-card-text>
                Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare.
              </v-card-text>
              <v-list class="transparent">
                <v-list-tile>
                  <v-list-tile-action>
                    <v-icon class="blue--text text--lighten-2">phone</v-icon>
                  </v-list-tile-action>
                  <v-list-tile-content>
                    <v-list-tile-title>777-867-5309</v-list-tile-title>
                  </v-list-tile-content>
                </v-list-tile>
                <v-list-tile>
                  <v-list-tile-action>
                    <v-icon class="blue--text text--lighten-2">place</v-icon>
                  </v-list-tile-action>
                  <v-list-tile-content>
                    <v-list-tile-title>Chicago, US</v-list-tile-title>
                  </v-list-tile-content>
                </v-list-tile>
                <v-list-tile>
                  <v-list-tile-action>
                    <v-icon class="blue--text text--lighten-2">email</v-icon>
                  </v-list-tile-action>
                  <v-list-tile-content>
                    <v-list-tile-title>john@vuetifyjs.com</v-list-tile-title>
                  </v-list-tile-content>
                </v-list-tile>
              </v-list>
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
  }
}
</script>

<style>
  .btn {
    text-transform: none;
  }
</style>