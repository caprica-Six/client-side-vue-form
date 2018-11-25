<template>
    <section class="section is-medium">
      <div class="container">
          <h1 class="title has-text-centered">Client side form with Vue.js, Bulma and Vuelidate</h1>

          <div class="columns is-mobile is-centered">
              <div class="column is-half">
                  <form v-if="!isSubmitted"
                        class="form"
                        action=""
                        method="post"
                        role="form"
                        name="contact">

                      <div class="field" :class="{ 'form-group--error': $v.name.$error }">
                          <label class="label" for="name">Name</label>
                          <div class="control">
                              <input v-model="name"
                                     @blur="$v.name.$touch()"
                                     class="input"
                                     type="text"
                                     name="name"
                                     id="name"
                                     placeholder="Name">
                              <div class="error" v-if="$v.name.$error">Name must have at least {{$v.name.$params.minLength.min}} letters.</div>
                          </div>
                      </div>

                      <div class="field" :class="{ 'form-group--error': $v.email.$error }">
                          <label class="label" for="email">Email</label>
                          <div class="control">
                              <input class="input"
                                     v-model="email"
                                     @blur="$v.email.$touch()"
                                     type="text"
                                     name="email"
                                     id="email"
                                     placeholder="Email">
                              <div class="error" v-if="$v.email.$error">Please provide a valid email.</div>
                          </div>
                      </div>

                      <div class="field" :class="{ 'form-group--error': $v.message.$error }">
                          <label class="label">Message</label>
                          <div class="control">
                          <textarea class="textarea"
                                    placeholder="Your message ..."
                                    v-model="message"
                                    @blur="$v.message.$touch()"
                                    name="message"
                                    id="message"
                                    rows="10">
                          </textarea>
                              <div class="error" v-if="$v.message.$error">Your message is required.</div>
                          </div>
                      </div>

                      <div class="control">
                          <button
                                  type="submit"
                                  @click.prevent="submitted"
                                  :disabled="$v.$invalid"
                                  class="button is-primary">
                              Submit
                          </button>
                      </div>
                  </form>

                  <div v-if="isSubmitted">
                      <h4 class="has-text-centered bd-footer-title">Thank you ...</h4>
                  </div>
              </div>
          </div>
      </div>
    </section>
</template>

<script>
    import { required, minLength, email } from 'vuelidate/lib/validators'
export default {
  name: 'AppForm',

    data() {
      return {
          name: '',
          email: '',
          message: '',
          isSubmitted: false
      }
    },

    validations: {
        name: {
            required,
            minLength: minLength(4)
        },
        email: {
            required,
            email
        },
        message: {
            required
        }
    },

    methods: {
      submitted() {
          this.isSubmitted = true
        }
    }

}
</script>

<style scoped>
    .title {
        font-weight: 400;
    }

    .form {
        background: white;
        box-shadow: 0 4px 6px rgba(50,50,93,.11), 0 1px 3px rgba(0,0,0,.08);
        padding: 2rem;
    }

    label {
        font-weight: 400;
    }

    /* Form validation */

    .form-group--error label {
        color: #ff3043;
    }

    .form-group--error input {
        background: #ffdee1;
        border: 1px solid #ff3043;
    }

    .error {
        background: transparent;
        color: #ff3440;
        font-size: .875em;
        margin-top: 5px;
    }

    input,
    textarea{
        transition: border-color .2s cubic-bezier(.645,.045,.355,1)
    }

</style>
