<template>
  <v-row>
    <v-col cols="12" lg="7" xl="6" class="info d-none d-md-flex align-center justify-center">
      <v-container>
        <div class="pa-10">
          <v-row justify="center">
            <v-col cols="8" xl="5">
              <div>
                <h2
                  class="display-1 white--text font-weight-medium"
                >MarkDown Project</h2>
                <h6
                  class="subtitle-1 mt-4 white--text op-5 font-weight-regular"
                >Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.</h6>
<!--                <v-btn class="mt-4 text-capitalize" x-large outlined color="white">Learn More</v-btn>-->
              </div>
            </v-col>
          </v-row>
        </div>
      </v-container>
    </v-col>
    <v-col cols="12" lg="5" xl="6" class="d-flex align-center">
      <v-container>
        <div class="pa-7 pa-sm-12">
          <v-row>
            <v-col cols="12" lg="9" xl="6">
              <img src="@/assets/images/logo-icon.png" />
              <h2 class="font-weight-bold mt-4 blue-grey--text text--darken-2">Entrar</h2>
              <h6 class="subtitle-1">
                ¿No tienes una cuenta?
                <a href="/authentication/fullregister/" class>Registrate!</a>
              </h6>

              <v-form ref="form" v-model="valid" lazy-validation action="/dashboards/analytical">
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="E-mail"
                  class="mt-4"
                  required
                  outlined
                ></v-text-field>
                <v-text-field
                  v-model="password"
                  :counter="10"
                  :rules="passwordRules"
                  label="Password"
                  required
                  outlined
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  :type="show1 ? 'text' : 'password'"
                  @click:append="() => (show1 = !show1)"
                ></v-text-field>

                <div class="d-block d-sm-flex align-center mb-4 mb-sm-0">
<!--                  <v-checkbox-->
<!--                    v-model="checkbox"-->
<!--                    :rules="[v => !!v || 'You must agree to continue!']"-->
<!--                    label="Remember me?"-->
<!--                    required-->
<!--                  ></v-checkbox>-->
                  <div class="ml-auto">
                    <a href="/authentication/fullrecovery/" class="link">¿Olvidaste tu password?</a>
                  </div>
                </div>
                <br>
                <v-btn
                  :disabled="!valid"
                  color="info"
                  block
                  class="mr-4"
                  submit
                  @click="submit"
                >Entrar</v-btn>
              </v-form>
              <div class="text-center mt-6">
                <v-chip pill class="mr-2">
                  <v-avatar left>
                    <v-btn color="blue lighten-1" class="white--text">
                      <v-icon>mdi-twitter</v-icon>
                    </v-btn>
                  </v-avatar>Twitter
                </v-chip>
                <v-chip pill>
                  <v-avatar left>
                    <v-btn color="teal lighten-2" class="white--text">
                      <v-icon>mdi-github</v-icon>
                    </v-btn>
                  </v-avatar>Github
                </v-chip>
              </div>
            </v-col>
          </v-row>
        </div>
      </v-container>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "FullLogin",
  data: () => ({
    valid: true,
    password: "",
    show1: false,
    passwordRules: [
      v => !!v || "Password es necesario",
      v => (v && v.length <= 10) || "Password no debe ser mayor a 10 caracteres"
    ],
    email: "",
    emailRules: [
      v => !!v || "E-mail es necesario",
      v => /.+@.+\..+/.test(v) || "Ingrese un E-mail valido, por ejemplo: example@example.ex"
    ],
    checkbox: false
  }),
  methods: {
    submit() {
      this.$refs.form.validate();
      if (this.$refs.form.validate(true)) {
        this.$router.push({ path: "/dashboards/analytical" });
      }
    }
  }
};
</script>
