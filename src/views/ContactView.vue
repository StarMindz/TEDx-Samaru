<template>
  <div>
    <div class="form">
      <div class="container">
        <div class="contact-section">
          <div class="wrapper">
            <h2>Contact Us</h2>
            <p>Our friendly team would love to hear from you.</p>
            <div>
              <form action="https://formspree.io/f/xkndyqzl" method="POST">
                <div class="contact-form">
                  <div class="input-group">
                    <FormInput class="form-group" :name="'First Name'" :label="'First Name'" :placeholder="'First Name'"
                      v-model="form.firstName"></FormInput>
                    <FormInput class="form-group" :name="'Last Name'" :label="'Last Name'" :placeholder="'Last Name'"
                      v-model="form.lastName"></FormInput>
                  </div>

                  <FormInput class="form-group" :name="'Email'" :label="'Email'" :placeholder="'Email'"
                    v-model="form.email" type="email"></FormInput>
                  <FormInput class="form-group"  :name="'Phone Number'" :label="'Phone Number'"
                    :placeholder="'Phone Number'" v-model="form.phoneNumber" type="tel"></FormInput>
                </div>
                <div class="form-group">
                  <label for="message">Message:</label>
                  <textarea id="message" required name="message" rows="5" placeholder="Write your message here"
                    v-model="form.message"></textarea>
                </div>
                <div class="form-group">
                  <input type="checkbox" required id="privacy" name="privacy" v-model="form.agreedToPolicy" />
                  <label for="privacy">I agree to the Privacy Policy</label>
                </div>
                <div>
                  <button class="submit-btn" @click="handleSubmit">Send Message</button>
                </div>
              </form>
            </div>
          </div>
          <img class="image" src="/src/assets/images/contact-Image.png" />
        </div>
      </div>
    </div>
    <div class="faq"></div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'
import FormInput from '../components/form-inputs/Input.vue'

const form = reactive({
  firstName: '',
  lastName: '',
  email: '',
  phoneNumber: '',
  message: '',
  agreedToPolicy: false
})

// const handleSubmit = () => {
//   // sendEmail()
// }

// const sendEmail = () => {
//   import('https://smtpjs.com/v3/smtp.js').then((module) => {
//     module.default
//       .send({
//         Host: 'smtp.elasticemail.com',
//         Username: 'username',
//         Password: 'password',
//         To: 'them@website.com',
//         From: 'you@isp.com',
//         Subject: 'This is the subject',
//         Body: 'And this is the body'
//       })
//       .then((message) => alert(message))
//   })
// }
</script>

<style lang="scss" scoped>
@use '../assets/css/variables' as v;
@use '../assets/css/mixin' as m;

.faq {
  margin-block: 5rem;
}

.submit-btn {
  width: 100%;
  text-align: center;
  @include m.btn(v.$White,
        v.$black,
        v.$red,
        v.$red,
        v.$White,
        v.$White,
        v.$black )
}

.contact-form {
  display: flex;
  flex-direction: column;

  .input-group {
    display: flex;
    flex-direction: row;
    gap: 0.5rem;
  }
}

textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 3px;
  resize: vertical;
}

input[type='checkbox'] {
  margin-right: 5px;
}

.form-group {
  margin-bottom: 15px;
  width: 100%;
}

label {
  margin-bottom: 0.5rem;
}

.text-input {
  padding: 1rem;
  border-radius: 0.5rem;
}

.contact-section {
  display: flex;
  flex-direction: row;
  justify-content: space-between;

  .wrapper {
    margin-block: 20px 48px;
    padding: 3rem;
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }

  .image {
    box-shadow:
      0 12px 24px rgba(0, 0, 0, 0.12),
      0 8px 16px rgba(0, 0, 0, 0.08);
    transition: box-shadow 0.3s ease-in-out;
    border-radius: 8px;
    overflow: hidden;
  }

  .image:hover {
    box-shadow:
      0 20px 30px rgba(0, 0, 0, 0.18),
      0 12px 22px rgba(0, 0, 0, 0.12);
  }

  @media screen and (max-width: 768px) {
    .wrapper {
      padding: 0rem;
    }

    .input-group {
      flex-direction: column;
    }

    img {
      display: none;
    }
  }
}
</style>
