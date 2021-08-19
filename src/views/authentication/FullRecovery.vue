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
              <h2 class="font-weight-bold mt-4 blue-grey--text text--darken-2">Recuperar Contraseña</h2>
              <h6 class="subtitle-1">
                ¿Ya tienes una cuenta registrada?
                <a href="/authentication/fulllogin/" class>Ingresa!</a>
              </h6>
              <br>

              <v-form ref="form" v-model="valid" lazy-validation action="/pages/boxedlogin">

                <v-text-field v-model="email" :rules="emailRules" label="E-mail" required outlined></v-text-field>

                <v-btn
                  :disabled="!valid"
                  color="info"
                  block
                  class="mr-4"
                  submit
                  @click="submit"
                >Recuperar contraseña</v-btn>
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
    email: "",
    emailRules: [
      v => !!v || "E-mail es necesario",
      v => /.+@.+\..+/.test(v) || "Ingrese un E-mail valido, por ejemplo: example@example.ex"
    ],
  }),
  methods: {
    submit() {
      this.$refs.form.validate();
      if (this.$refs.form.validate(true)) {
        this.$router.push({ path: "/authentication/fulllogin" });
      }
    }
  }
};
</script>
