<template>
  <div
    class="py-5 p-st"
    :class="{
      'bg-light': !nightMode,
      'bg-dark2': nightMode,
      'text-light': nightMode,
    }"
  >
    <div class="container">
      <div
        class="text-center mb-4"
        data-aos="fade"
        data-aos-once="true"
        data-aos-duration="1000"
      >
        <h2 class="title" :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
          Contact
        </h2>
        <hr
          width="60"
          class="mx-auto"
          :class="{ 'bg-secondary': nightMode, 'pgray': !nightMode }"
        />
      </div>

      <form class="text-center">
        <div
          class="form-group"
          data-aos="fade-up"
          data-aos-delay="100"
          data-aos-duration="1000"
        >
          <input
            v-model="name"
            type="text"
            placeholder="Your name"
            class="pinput-modern"
            :class="{ 'text-light': nightMode }"
          />
        </div>

        <div
          class="form-group"
          data-aos="fade-up"
          data-aos-delay="200"
          data-aos-duration="1000"
        >
          <input
            v-model="email"
            type="email"
            placeholder="Your email"
            class="pinput-modern"
            :class="{ 'text-light': nightMode }"
          />
        </div>

        <div
          class="form-group"
          data-aos="fade-up"
          data-aos-delay="300"
          data-aos-duration="1000"
        >
          <textarea
            v-model="text"
            rows="5"
            placeholder="Your message"
            class="pinput-modern"
            :class="{ 'text-light': nightMode }"
          ></textarea>
        </div>

        <button
          @click.prevent="sendEmail"
          class="btn-modern"
          data-aos="zoom-in"
          data-aos-delay="400"
        >
          Send Message
        </button>
      </form>

      <Snackbar
        :showSnackbar="showSnackbar"
        @close="closeSnackbar"
        :snackbarMessage="snackbarMessage"
        :snackbarColor="snackbarColor"
      />
    </div>
  </div>
</template>

<script>
import config from "../../config";
import emailjs from "emailjs-com";
import Snackbar from "./helpers/Snackbar";

export default {
  name: "Contact",
  components: { Snackbar },
  props: {
    nightMode: Boolean,
  },
  data() {
    return {
      email: "",
      name: "",
      text: "",
      showSnackbar: false,
      snackbarMessage: "",
      snackbarColor: "",
    };
  },
  methods: {
    closeSnackbar(val) {
      if (!val) {
        setTimeout(() => {
          this.showSnackbar = val;
        }, 1000);
      }
    },
    sendEmail() {
      if (!this.email || !this.name || !this.text) {
        this.showSnackbar = true;
        this.snackbarMessage = "Please fill all the fields";
        this.snackbarColor = "#64808E";
      } else {
        const obj = {
          user_email: this.email,
          from_name: this.name,
          message_html: this.text,
          to_name: "Muhammad Rizki Pratama",
        };

        emailjs
          .send(
            config.emailjs.serviceID,
            config.emailjs.templateID,
            obj,
            config.emailjs.userID
          )
          .then(
            () => {
              this.showSnackbar = true;
              this.snackbarMessage = "Thanks! Message received.";
              this.snackbarColor = "#1aa260";
              this.email = "";
              this.text = "";
              this.name = "";
            },
            () => {
              this.showSnackbar = true;
              this.snackbarMessage = "Oops! Something went wrong.";
              this.snackbarColor = "#e74c3c";
            }
          );
      }
    },
  },
};
</script>

<style scoped>
.title {
  font-size: 32px;
  font-weight: 600;
}

/* Input Modern Style */
.pinput-modern {
  width: 100%;
  max-width: 600px;
  padding: 14px 18px;
  font-size: 16px;
  border-radius: 12px;
  border: none;
  margin: 10px auto;
  background: #f0f0f0;
  transition: all 0.3s ease;
  box-shadow: inset 2px 2px 6px #ccc, inset -2px -2px 6px #fff;
}

.pinput-modern:focus {
  outline: none;
  box-shadow: 0 0 8px #759CC9;
  background: #ffffff;
}

/* Dark mode override */
.bg-dark2 .pinput-modern {
  background: #2f2f2f;
  color: #eee;
  box-shadow: inset 2px 2px 5px #1f1f1f, inset -2px -2px 5px #444;
}
.bg-dark2 .pinput-modern:focus {
  background: #3c4148;
  box-shadow: 0 0 10px #00f0ff;
}

/* Button style */
.btn-modern {
  background-color: #759cc9;
  color: white;
  padding: 12px 40px;
  font-size: 16px;
  border-radius: 8px;
  border: none;
  transition: all 0.3s ease-in-out;
}
.btn-modern:hover {
  background-color: #5b87c1;
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(117, 156, 201, 0.3);
}

.form-group {
  margin-bottom: 20px;
}
</style>
