<template>
  <v-container>
    <v-container fluid fill-height>
      <v-layout align-center justify-center>
        <v-flex xs12 sm8 md6>
          <v-card class="elevation-12">
            <v-toolbar dark color="Black">
              <v-toolbar-title>Регистрация</v-toolbar-title>
              <v-spacer></v-spacer>
              <v-tooltip right>
                <template v-slot:activator="{ on }">
                  <v-btn icon large href="https://codepen.io/johnjleider/pen/wyYVVj" target="_blank" v-on="on">
                    <v-icon large>mdi-codepen</v-icon>
                  </v-btn>
                </template>
                <span>Codepen</span>
              </v-tooltip>
            </v-toolbar>
            <v-card-text>
              <v-form
                v-model="valid"
                ref="form"
                lazy-validation>
                <v-text-field id="moika"
                              prepend-icon="business"
                              name="Moika"
                              label="Название мойки"
                              type="text"
                              v-model="moika">

                </v-text-field>
                <v-text-field id="name"
                              prepend-icon="face"
                              name="Name"
                              label="Имя"
                              type="text"
                              v-model="name"
                              :rules="NameRules">

                </v-text-field>
                <v-text-field id="surname"
                              prepend-icon="perm_identity"
                              name="Surname"
                              label="Фамилия"
                              type="text"
                              v-model="surname"
                              :rules="SurnameRules">

                </v-text-field>
                <v-text-field id="city"
                              prepend-icon="location_city"
                              name="City"
                              label="Город"
                              type="text"
                              v-model="city"
                              :rules="CityRules">

                </v-text-field>
                <v-text-field id="phone"
                              prepend-icon="call"
                              name="Phone"
                              label="Телефон"
                              type="text"
                              v-model="phone"
                              :rules="PhoneRules">

                </v-text-field>
                <v-text-field id="password"
                              prepend-icon="lock"
                              name="password"
                              label="Пароль"
                              type="password"
                              v-model="password"
                              :rules="PasswordRules">

                </v-text-field>
                <v-text-field id="password1"
                              prepend-icon="subdirectory_arrow_right"
                              name="password2"
                              label="Подтвердите пароль"
                              type="password"
                              v-model="password2"
                              :rules="password2Rules">

                </v-text-field>
              </v-form>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn
                color="primary"
                @click="onSubmit"
                :disabled="!valid">
                Подтвердить</v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </v-container>
</template>

<script>
  export default {
    name: "Reg.vue",
    data(){
      return {
        number: '',
        password: '',
        password2: '',
        moika:'',
        name:'',
        surname:'',

        valid: false,
        PhoneRules:[
          v => !!v ||'Попробуйте ещё раз',
          v =>/^(\s*)?(\+)?([- _():=+]?\d[- _():=+]?){10,14}(\s*)?$/.test(v) || 'Попробуйте ещё раз'
        ],
        PasswordRules:[
          v => !!v ||'Попробуйте ещё раз',
          v =>/(?=^.{8,30}$)((?=.*\d)|(?=.*\W+))(?![.\n])(?=.*[a-z]).*$/.test(v) ||'Попробуйте ещё раз'

        ],
        NameRules:[
          v => !!v ||'Попробуйте ещё раз',
          v =>/^[а-яА-ЯёЁ]+$/.test(v) || 'Введите настоящее имя'
        ],
        SurnameRules:[
          v => !!v ||'Попробуйте ещё раз',
          v =>/^[а-яА-ЯёЁ]+$/.test(v) || 'Введите настоящую фамилию'
        ],
        CityRules:[
          v => !!v ||'Попробуйте ещё раз',
          v =>/^[а-яА-ЯёЁ]+$/.test(v) || 'Проверьте правильность написания'
        ],
        Password2Rules:[
          v => !!v ||'Попробуйте ещё раз',
          v => v === this.password  ||'Попробуйте ещё раз'
          ],
      }
    },
    methods: {
      onSubmit (){
        if (this.$refs.form.validate()) {
          const user = {
            moika: this.moika,
            name: this.name,
            surname: this.name,
            city: this.city,
            phone: this.phone,
            password: this.password,
          }
          console.log(user)
        }
      }
    }
  }
</script>

<style scoped>

</style>
