<template>
    <section class="section is-medium">
      <div class="container">
          <h1 class="title">Client side form with Vue.js, Bulma and Vuelidate</h1>

          <div class="columns">
              <div class="column is-full">
                  <form class="form">
                      <div class="field">
                          <label class="label">Name</label>
                          <div class="control">
                              <input class="input"
                                     type="text"
                                     placeholder="Name">
                          </div>
                      </div>

                      <div class="field">
                          <label class="label">Email</label>
                          <div class="control">
                              <input class="input"
                                     type="email"
                                     placeholder="Email"
                                     value="">
                          </div>
                      </div>

                      <div class="field">
                          <label class="label">Message</label>
                          <div class="control">
                      <textarea class="textarea"
                                placeholder="Your message">
                      </textarea>
                          </div>
                      </div>

                      <div class="control">
                          <button class="button is-primary">Submit</button>
                      </div>
                  </form>
              </div>
          </div>


      </div>
    </section>
</template>

<script>
export default {
  name: 'ApppForm'
}
</script>

<style scoped>
    .title {
        text-align: center;
    }

    .form {
        background: white;
        box-shadow: 0 6px 15px rgba(36,37,38,0.08);
        max-width: 25em;
        margin: auto;
        padding: 2rem;
    }

    label {
        font-weight: 400;
    }
</style>
