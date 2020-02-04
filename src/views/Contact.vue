<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Contact</h1>
        <template>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-text-field
              v-model="name"
              :counter="10"
              :rules="nameRules"
              label="Name"
              required
            ></v-text-field>

            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="E-mail"
              required
            ></v-text-field>

            <v-select
              v-model="select"
              :items="items"
              :rules="[v => !!v || 'Item is required']"
              label="Item"
              required
            ></v-select>

            <v-checkbox
              v-model="checkbox"
              :rules="[v => !!v || 'You must agree to continue!']"
              label="Do you agree?"
              required
            ></v-checkbox>

            <!-- <v-btn
              :disabled="!valid"
              color="success"
              class="mr-4"
              @click="validate"
            >
              Validate
            </v-btn>

            <v-btn color="error" class="mr-4" @click="reset">
              Reset Form
            </v-btn> -->
            <v-btn class="mr-4" color="success" @click="submit">submit</v-btn>

            <v-btn class="mr-4" @click="clear">clear</v-btn>

            <!-- <v-btn color="warning" @click="resetValidation">
              Reset Validation
            </v-btn> -->
          </v-form>
        </template>
      </v-col>
    </v-row>
  </v-container>
</template>
<!-- <v-card width="400" class="mx-auto mt-5">
    <v-card-title class="pb-0">
      <h1 class="display-1">Contact</h1>
    </v-card-title>
    <v-card-text>
      <v-form>
        <v-text-field 
          label="Username" 
          prepend-icon="mdi-account-circle"
        />
        <v-text-field 
          :type="showPassword ? 'text' : 'password'" 
          label="Password"
          prepend-icon="mdi-lock"
          :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append="showPassword = !showPassword"
        />
      </v-form>
    </v-card-text>
    <v-divider></v-divider>
    <v-card-actions>
      <v-btn color="success">Register</v-btn>
      <v-spacer></v-spacer>
      <v-btn color="info">Contact</v-btn>
    </v-card-actions>
  </v-card>
</template> -->

<script>
  export default {
    data: () => ({
      valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      select: null,
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4',
      ],
      checkbox: false,
    }),

    methods: {
      validate () {
        if (this.$refs.form.validate()) {
          this.snackbar = true
        }
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
  }
</script>
//
<script>
// export default {
//   name: 'Contact',
//   data() {
//     return {
//       showPassword: false
//     }
//   }
// }
//
</script>
