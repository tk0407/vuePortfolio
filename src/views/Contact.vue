<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Contact</h1>
        <template>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-text-field
              v-model="name"
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

            <v-textarea
              v-model="message"
              v-validate="'required|max:100'"
              :counter="100"
              label="Message"
              required
              :rules="messageRules"
            ></v-textarea>

            <v-btn
              class="mr-9"
              :disabled="!valid"
              color="success"
              @click="submit"
              >submit</v-btn
            >
          </v-form>
        </template>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    valid: true,
    name: "",
    nameRules: [v => !!v || "Name is required"],
    email: "",
    emailRules: [
      v => !!v || "E-mail is required",
      v => /.+@.+\..+/.test(v) || "E-mail must be valid"
    ],
    message: "",
    messageRules: [
      v => !!v || "Message is required",
      v => (v && v.length <= 100) || "Max 100 characters"
    ]
  }),

  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        this.snackbar = true;
      }
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    }
  }
};
</script>
