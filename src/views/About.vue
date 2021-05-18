<template>
  <v-container fluid>
    <v-row>
      <v-col>
        <v-card>
          <v-card-title>Обо мне</v-card-title>
          <v-card-text>
            Возраст: {{AGE()}} года<br>
            Образование: среднее специальное, специальность: программирование в компьютерных системах<br>
            Ключевые навыки: HTML/CSS | JavaScript ES6+ | Vue.js | Git
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-row>
      <v-col class="d-flex justify-center" v-for="skill in About">
        <v-card width="300" min-height="300">
          <v-card-title>{{skill.skill}}</v-card-title>
          <v-card-text>{{skill.desc}}</v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    const About = [
      {skill: 'HTML', desc: 'Умею применять технологии Flexbox, Grid, медиазапросы. Понимаю анимации и трансформации. Умею верстать адаптивно с помощью Bootstrap'},
      {skill: 'JavaScript', desc: 'Знаком с современным синтаксисом EcmaScript 6 и новее. Умею работать с асинхронным кодом'},
      {skill: 'Vue', desc: 'Умею работать с последней 3й версией, пользоваться Vuex, Vue router, создавать приложения через Vue CLI, знаю основы Vuetify'},
      {skill: 'А также', desc: 'Знаю основы языков программирования C# и Python, основы СКВ Git, основы React.js'}
    ]
    const AGE = () => {
      const now = new Date()
      const today = new Date(now.getFullYear(), now.getMonth(), now.getDate())
      const birth = new Date(1998, 8, 11)
      const birthnow = new Date(today.getFullYear(), birth.getMonth(), birth.getDate())
      let age
      age = today.getFullYear() - birth.getFullYear();
      if (today < birthnow) age = age-1
      return age
    }
    return {
      About,
      AGE
    }
  }
}
</script>
