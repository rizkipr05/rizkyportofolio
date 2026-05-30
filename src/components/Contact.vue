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
        <span class="section-kicker">Let's build something</span>
        <h2 class="title" :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
          Contact
        </h2>
        <hr
          width="60"
          class="mx-auto"
          :class="{ 'bg-secondary': nightMode, 'pgray': !nightMode }"
        />
      </div>

      <form class="text-center contact-shell">
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
  font-size: 2.4rem;
  font-weight: 700;
}

.section-kicker {
  display: inline-block;
  padding: 0.45rem 0.85rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.12);
  color: #0369a1;
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 10px;
}

.contact-shell {
  max-width: 760px;
  margin: 0 auto;
  padding: 30px;
  border-radius: 28px;
  background: rgba(255, 255, 255, 0.6);
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 24px 60px rgba(15, 23, 42, 0.08);
}

.pinput-modern {
  width: 100%;
  max-width: 100%;
  padding: 16px 18px;
  font-size: 16px;
  border-radius: 18px;
  border: 1px solid rgba(148, 163, 184, 0.18);
  margin: 10px auto;
  background: rgba(255, 255, 255, 0.8);
  transition: all 0.3s ease;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.8);
}

.pinput-modern:focus {
  outline: none;
  border-color: rgba(14, 165, 233, 0.42);
  box-shadow: 0 0 0 4px rgba(14, 165, 233, 0.12);
  background: #ffffff;
}

.bg-dark2 .contact-shell {
  background: rgba(255, 255, 255, 0.04);
  border-color: rgba(148, 163, 184, 0.12);
}

.bg-dark2 .pinput-modern {
  background: rgba(255, 255, 255, 0.04);
  color: #eee;
  border-color: rgba(148, 163, 184, 0.12);
  box-shadow: none;
}
.bg-dark2 .pinput-modern:focus {
  background: rgba(255, 255, 255, 0.06);
  box-shadow: 0 0 0 4px rgba(34, 211, 238, 0.12);
}

.btn-modern {
  background: linear-gradient(135deg, #0ea5e9, #2563eb);
  color: white;
  padding: 14px 40px;
  font-size: 16px;
  font-weight: 700;
  border-radius: 999px;
  border: none;
  transition: all 0.3s ease-in-out;
  box-shadow: 0 22px 42px rgba(37, 99, 235, 0.22);
}
.btn-modern:hover {
  transform: translateY(-2px);
  box-shadow: 0 26px 50px rgba(37, 99, 235, 0.3);
}

.form-group {
  margin-bottom: 20px;
}

@media screen and (max-width: 580px) {
  .contact-shell {
    padding: 20px;
    border-radius: 22px;
  }
}
</style>
