<template>
  <div class="lg:flex items-center mx-auto px-8 max-w-6xl">
    <div class="mb-6 lg:mr-20">
      <h1>Hello World!</h1>
      <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Odio rerum
        blanditiis in fuga et odit accusamus repellendus, officia reprehenderit
        cum dolorum fugit! Sed, hic voluptatum odit corporis reiciendis quo
        cupiditate.
      </p>
      <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Odio rerum
        blanditiis in fuga et odit accusamus repellendus, officia reprehenderit
        cum dolorum fugit! Sed, hic voluptatum odit corporis reiciendis quo
        cupiditate.
      </p>
      <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Odio rerum
        blanditiis in fuga et odit accusamus repellendus, officia reprehenderit
        cum dolorum fugit! Sed, hic voluptatum odit corporis reiciendis quo
        cupiditate.
      </p>
    </div>
    <form
      name="contact"
      action="/sent/"
      method="POST"
      netlify-honeypot="bot-field"
      data-netlify-recaptcha="true"
      data-netlify="true"
    >
      <input type="hidden" name="contact-form" value="contact" />
      <label for="person-name">Name</label>
      <input id="name-field" type="text" name="person-name" required />
      <label for="email">Email</label>
      <input id="email-field" type="email" name="email" required />
      <label for="message">Message</label>
      <textarea
        id="message-field"
        name="message"
        cols="30"
        rows="10"
        required
      ></textarea>
      <p class="hidden">
        <label class="hidden">
          Don’t fill this out if you’re human:
          <input name="bot-field" />
        </label>
      </p>
      <div data-netlify-recaptcha="true"></div>
      <div
        class="g-recaptcha mb-6"
        :data-sitekey="$config.SITE_RECAPTCHA_KEY"
      />
      <button id="send-it" type="submit">Send</button>
    </form>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  head: {
    title: 'About | Kai Asuncion',
    meta: [
      {
        hid: 'description',
        name: 'description',
        content: '',
      },
      {
        hid: 'description',
        name: 'description',
        content: '',
      },
      // Open Graph
      {
        hid: 'og:title',
        property: 'og:title',
        content: '',
      },
      {
        hid: 'og:description',
        property: 'og:description',
        content: '',
      },
      // Twitter Card
      {
        hid: 'twitter:title',
        name: 'twitter:title',
        content: '',
      },
      {
        hid: 'twitter:description',
        name: 'twitter:description',
        content: '',
      },
    ],
    script: [{ src: 'https://www.google.com/recaptcha/api.js' }],
  },
})
</script>

<style>
p {
  @apply text-xl;
}
form {
  @apply w-full flex flex-col;
}
label {
  @apply text-xl;
}
input,
textarea {
  border: 1px solid var(--border-color);
  background-color: var(--bg);

  @apply mb-6 p-4 text-xl tracking-wide;
}
#send-it {
  border: 1px solid var(--border-color);
  transition: 0.3s;

  @apply p-4;
}
#send-it:hover {
  cursor: pointer;
  background-color: var(--color);
  color: var(--bg);
}
</style>
