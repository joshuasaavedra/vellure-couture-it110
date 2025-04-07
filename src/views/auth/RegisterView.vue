<script setup>
import { ref } from 'vue'

const theme = ref('light')
const email = ref('')
const phone = ref('')
const password = ref('')

function onClick() {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
}

function handlePhoneInput(event) {
  // Only allow numbers in the phone number field
  event.target.value = event.target.value.replace(/[^0-9]/g, '')
}
</script>


<template>
<v-responsive class="border rounded">
    <v-app :theme="theme">
      <v-app-bar class="px-3" color="teal-darken-4">
        <v-spacer></v-spacer>

        <v-btn
          :prepend-icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
          text="Toggle Theme"
          slim
          @click="onClick"
        ></v-btn>
      </v-app-bar>

      <v-main>
        <v-container>
          <v-row no-gutters class="d-flex">
            <!-- Login Card with Drop Shadow -->
            <v-col cols="12" md="6" class="d-flex align-center pa-0">
              <v-card class="mx-auto" elevation="8" outlined>
                <template v-slot:title>
                  <span class="font-weight-black text-teal-darken-4">Register to Vellure Couture!</span>
                </template>

                <!-- Form with Email, Phone, and Password -->
                <v-card-text class="bg-surface-light pt-4">
                  <v-form fast-fail @submit.prevent>
                    <v-text-field label= "Firstname"  variant="outlined"></v-text-field>

                    <v-text-field label= "Lastname"  variant="outlined"></v-text-field>
                    <!-- Email Field -->
                    <v-text-field
                      label="Email"
                       variant="outlined"
                    ></v-text-field>

                    <!-- Phone Number Field (Only Numbers) -->
                    <v-text-field
                      label="Phone Number"
                       variant="outlined"
                      type="tel"
                      @input="handlePhoneInput"
                    ></v-text-field>

                    <!-- Password Field -->
                    <v-text-field
                      label="Password"
                      type="password"
                      variant="outlined"
                    ></v-text-field>

                    <v-text-field
                      label="Password confirmation"
                      type="password"
                      variant="outlined"
                    ></v-text-field>

                    <!-- Login Button -->
                    <v-btn class="mt-2" type="submit" block color="teal-darken-4">Login</v-btn>

                    <!-- Register Text Below Button (Smaller Text, No Box) -->

                  </v-form>
                  <v-divider class="my-5"></v-divider>

                   <h5 class="text-center">
                    Already have account?<RouterLink to ="/">Click here to Login</RouterLink>
                </h5>
                </v-card-text>
              </v-card>
            </v-col>

            <!-- Image on the Right with Drop Shadow -->
            <v-col cols="12" md="6" class="pa-0">
              <v-img
                src="/images/vellure-couture.png"
                alt="Login Image"
                aspect-ratio="1"
                contain
              ></v-img>
            </v-col>
          </v-row>
        </v-container>
      </v-main>

      <v-footer class="d-flex justify-center" color="teal-darken-4" border app>2025 - Vellure Couture</v-footer>
    </v-app>
  </v-responsive>

</template>
