<template>
  <v-app>
    <div class="form-upper">
      <v-img
        class="form-image"
        :lazy-src="require('@/assets/images/logo.png?lqip')"
        height="auto"
        width="200"
        :src="require('@/assets/images/logo.png?webp')"
      />
      <h5>Start Investing Now!</h5>
    </div>
    <hr>
    <div>
      <v-form
        v-model="valid"
        accept-charset="UTF-8"
        method="POST"
        @submit.prevent="onSubmit()"
      >
        <v-container>
          <v-row>
            <v-col>
              <ValidationProvider v-slot="{errors}" rules="required|alpha|min:2">
                <v-text-field
                  v-model="firstname"
                  label="First name"
                  solo
                  rounded
                  :disabled="loading"
                  :error-messages="errors"
                  required
                />
              </ValidationProvider>
            </v-col>

            <v-col>
              <ValidationProvider v-slot="{errors}" rules="required|alpha|min:2">
                <v-text-field
                  v-model="lastname"
                  label="Last name"
                  solo
                  rounded
                  :disabled="loading"
                  :error-messages="errors"
                  required
                />
              </ValidationProvider>
            </v-col>
          </v-row>
          <v-row>
            <v-col>
              <ValidationProvider v-slot="{errors}" rules="required|email">
                <v-text-field
                  v-model="email"
                  label="Email Address"
                  solo
                  rounded
                  :disabled="loading"
                  :error-messages="errors"
                  required
                />
              </ValidationProvider>
            </v-col>
          </v-row>
          <v-row>
            <v-col>
              <div class="phoneField">
                <ValidationProvider style="width: 20%; margin-left: 10px;">
                  <select
                    v-model="submit"
                    style="margin-left: 20px; width: 50%;"
                    :disabled="loading"
                  >
                    <option value="BG">
                      BG
                    </option>
                    <option value="GB">
                      UK
                    </option>
                    <option value="US">
                      US
                    </option>
                  </select>
                </ValidationProvider>
                <ValidationProvider v-slot="{errors}" rules="required|numeric" style="width: 90%">
                  <v-text-field
                    v-model="phonenumber"
                    label="Phone Number"
                    required
                    rounded
                    :error-messages="errors"
                    :disabled="loading"
                  />
                </ValidationProvider>
              </div>
            </v-col>
          </v-row>
          <v-row>
            <v-col>
              <ValidationProvider v-slot="{errors}" rules="required|min:6">
                <v-text-field
                  v-model="password"
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  label="Password"
                  solo
                  rounded
                  :disabled="loading"
                  :error-messages="errors"
                  :type="show1 ? 'text' : 'password'"
                  name="input-10-1"
                  style="margin-top: 20px"
                >
                  <template slot="append">
                    <v-icon @click="show1 = !show1">
                      {{ show1 ? 'mdi-eye-off' : 'mdi-eye' }}
                    </v-icon>
                    <v-icon @click="generatePassword">
                      mdi-flash
                    </v-icon>
                  </template>
                </v-text-field>
              </ValidationProvider>
            </v-col>
          </v-row>
          <v-btn
            type="submit"
            class="purple--text font-weight-black text-lg-h6"
            color="#ff526ce0"
            :loading="loading"
            :disabled="loading"
            depressed
            rounded
            large
            width="inherit"
          >
            Get Started
            <v-icon class="purple--text text-lg-h5 ">
              mdi-cursor-default-click
            </v-icon>
          </v-btn>
          <p class="terms">
            All trading involves risk. Only risk capital you're prepared to lose. This site is protected by reCAPTCHA. Google Privacy Policy and Terms of Service apply.
          </p>
        </v-container>
      </v-form>
    </div>
  </v-app>
</template>

<script>
import { ValidationProvider } from 'vee-validate/dist/vee-validate.full.esm'
import libphonenumber from 'google-libphonenumber'
import { extend } from 'vee-validate'
import { required, email, alpha, min, numeric } from 'vee-validate/dist/rules.umd'
import axios from 'axios'
import generator from 'generate-password'
extend('min', min)
extend('numeric', numeric)
extend('required', required)
extend('email', email)
extend('alpha', alpha)
export default {
  components: { ValidationProvider },
  data () {
    return {
      show1: false,
      show2: true,
      show3: false,
      show4: false,
      valid: false,
      loader: null,
      loading: false,
      firstname: '',
      lastname: '',
      email: '',
      phonenumber: '',
      password: '',
      isSuccess: false,
      submit: 'BG'
    }
  },
  watch: {
    loader () {
      const l = this.loader
      this[l] = !this[l]
      setTimeout(() => (this[l] = false), 3000)

      this.loader = null
    }
  },
  methods: {
    onSubmit () {
      if (this.validate(this.phonenumber) === false) {
        alert('The entered number is invalid')
        return
      }
      if (this.firstname === '') {
        return
      }
      if (this.lastname === '') {
        return
      }
      if (this.email === '') {
        return
      }
      if (this.phonenumber === '') {
        return
      }
      if (this.password === '') {
        return
      }
      const data = {
        firstName: this.firstname,
        lastname: this.lastname,
        email: this.email,
        phonenumber: this.phonenumber,
        password: this.password
      }
      axios
        .post('https://httpbin.org/post', data, {
          headers: {
            Accept: 'application/json'
          }
        })
        .then((response) => {
          this.isSuccess = !!response.data.success
          // Disabling the no-console so the response can be displayed in the console as per requirement
          // eslint-disable-next-line no-console
          console.log(response)
        }, (response) => {
        })
      this.loader = 'loading'
    },
    generatePassword () {
      const passwordGenerator = generator.generate({
        length: Math.floor(Math.random() * 10) + 6,
        numbers: true,
        lowercase: true,
        uppercase: true
      })
      this.password = passwordGenerator
    },
    validate (value) {
      const phoneUtil = libphonenumber.PhoneNumberUtil.getInstance()
      const number = phoneUtil.parseAndKeepRawInput(value, this.submit)
      const isValid = phoneUtil.isValidNumberForRegion(number, this.submit)
      return isValid
    }
  }
}
</script>

  <style>
      .form-wrapper {
          background: #fff;
          width: 100%;
          margin-left: auto;
          margin-right: auto;
          border-radius: 4px;
          box-shadow: 0px 1px 15px -1px rgba(0,0,0,0.85);
          height: auto;
      }
      .form-image {
          margin-left: auto;
          margin-right: auto;
          margin-top: 10px;
          margin-bottom: 20px;
      }
      .form-upper {
          text-align: center;
      }
      .form-upper > h5 {
          color: #6018dc;
          margin-bottom: 20px;
          font-family: Arial, Helvetica, sans-serif;
          word-spacing: 1px;
          font-size: 20px;
      }
      .terms {
          color: gray;
          width: 100%;
          margin-top: 15px;
          font-family: 'Playfair Display', serif;
          font-size: 15px;;
      }
      .phoneField {
        display:flex;
        flex-direction: row;
        justify-content:flex-start;
        align-items: center;
        box-shadow: 0px 0.5px 4px 0px rgba(0,0,0,0.55);
        border-radius: 25px;
        height: 50px;
      }
      .custom-loader {
    animation: loader 1s infinite;
    display: flex;
  }
  @-moz-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-webkit-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-o-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  </style>
