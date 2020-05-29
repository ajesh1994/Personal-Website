<template>
  <div class="contactWrapper" id="contact">
    <div class="subHeadingWrapper">
      <h2 data-aos="fade-right" class="subHeading">Contact</h2>
      <div
        data-aos="fade-right"
        data-aos-anchor-placement="center-center"
        class="subHeadingUnderline"
      />
    </div>
    <div class="formWrapper" data-aos="fade-up">
      <form
        class="formFields"
        action="https://formspree.io/maypnzan"
        method="POST"
        @submit="checkForm"
      >
        <label class="labelLayout">
          Name:
          <input class="inputLayout" type="text" name="name" v-model="name" />
        </label>
        <label>
          Email:
          <input class="inputLayout" type="text" name="_replyto" v-model="email" />
        </label>
        <label class="messageField">
          Message:
          <textarea class="inputLayout textArea" name="message" v-model="message"></textarea>
        </label>

        <button class="submitButton" type="submit">Send</button>
      </form>
      <div class="errors" v-if="errors.length">
        <b>Please correct the following error(s):</b>
        <ul>
          <li v-for="error in errors" :key="error">{{ error }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {},
  data() {
    return {
      errors: [],
      name: null,
      email: null,
      message: null
    };
  },
  methods: {
    checkForm(e) {
      this.errors = [];

      if (!this.name) {
        this.errors.push("Name required.");
      }
      if (!this.email) {
        this.errors.push("Email required.");
      } else if (!this.validEmail(this.email)) {
        this.errors.push("Valid email required.");
      }

      if (!this.errors.length) {
        return true;
      }

      e.preventDefault();
    },
    validEmail(email) {
      const result = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return result.test(email);
    }
  }
};
</script>

<style scoped>
.inputLayout {
  display: block;
  border: 1px solid lightgrey;
  border-radius: 3px;
  width: 100%;
  height: 30px;
  padding: 6px 12px;
  margin-top: 5px;
}
.contactWrapper {
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
  padding: 50px 0;
}

.formWrapper {
  flex: 50%;
  font-family: OverpassBold;
}

.formFields > label {
  flex: 50%;
  padding: 10px 20px;
}

.formFields > label:nth-child(3) {
  flex: 100%;
}

.formFields {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  width: 80%;

  margin: auto;
}
.messageField {
  flex: 100%;
}

.subHeading {
  font-size: 50px;
  margin-bottom: 15px;
}
.subHeadingWrapper {
  flex: 15%;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin-bottom: 40px;
}

.errors {
  margin: auto;
  width: 270px;
  margin-top: 40px;
}
.subHeadingUnderline {
  border: 2px solid #7510f7;
  width: 75px;
}
.textArea {
  resize: none;
  width: 100%;
  height: 150px;
  padding: 6px 12px;
  margin-top: 5px;
}

.submitButton {
  border: #7510f7;
  background: #7510f7;
  border-radius: 25px;
  height: 50px;
  width: 100px;
  font-size: 16px;
  color: white;
  display: block;
  margin: 20px;
  font-family: OverpassBold;
}

.inputLayout:focus {
  border: 1px solid #7510f7;
}

.submitButton:focus {
  outline: 0;
  box-shadow: 0 0 0 0.2rem #7510f7;
}

.submitButton:hover {
  background: #5e07cd;
}

@media (min-width: 768px) {
  .formFields {
    width: 500px;
  }

  .subHeading {
    font-size: 66px;
  }
}
</style>
