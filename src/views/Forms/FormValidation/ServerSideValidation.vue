<template>
  <card>
    <!-- Card header -->
    <h3 slot="header" class="mb-0">Server side validation</h3>

    <!-- Card body -->
    <b-row>
      <b-col lg="8">
        <p class="mb-0">
          We recommend using client side validation, but in case you require server side, you can indicate invalid and
          valid form fields with <code>.is-invalid</code> and <code>.is-valid</code>. Note that
          <code>.invalid-feedback</code>
          is also supported with these classes.
        </p>
      </b-col>
    </b-row>
    <hr>
    <validation-observer v-slot="{handleSubmit}" ref="formValidator">
      <form class="needs-validation"
            @submit.prevent="handleSubmit(onSubmit)">
        <div class="form-row">
          <b-col md="4">
            <base-input label="First name"
                        rules="required"
                        name="First name"
                        placeholder="First name"
                        success-message="Looks good!"
                        v-model="model.firstName">
            </base-input>
          </b-col>

          <b-col md="4">
            <base-input label="Last name"
                        rules="required"
                        name="Last name"
                        placeholder="Last name"
                        success-message="Looks good!"
                        v-model="model.lastName">
            </base-input>
          </b-col>

          <b-col md="4">
            <base-input label="Username"
                        rules="required"
                        name="Username"
                        placeholder="Username"
                        success-message="Looks good!"
                        v-model="model.username">
            </base-input>
          </b-col>
        </div>
        <div class="form-row">
          <b-col md="6">
            <base-input label="City"
                        name="City"
                        rules="required"
                        placeholder="City"
                        success-message="Looks good!"
                        v-model="model.city">
            </base-input>
          </b-col>
          <b-col md="3">
            <base-input label="State"
                        name="State"
                        rules="required"
                        placeholder="State"
                        success-message="Looks good!"
                        v-model="model.state">
            </base-input>
          </b-col>
          <b-col md="3">
            <base-input label="Zip"
                        name="Zip"
                        rules="required"
                        placeholder="Zip"
                        success-message="Looks good!"
                        v-model="model.zip">
            </base-input>
          </b-col>
        </div>
        <base-input :rules="{ required: { allowFalse: false } }" name="Terms">
          <b-form-checkbox v-model="model.agree">
            Agree to terms and conditions
          </b-form-checkbox>
        </base-input>
        <base-button type="primary" native-type="submit">Submit form</base-button>
      </form>
    </validation-observer>
  </card>
</template>
<script>
  export default {
    components: {},
    data() {
      return {
        validated: false,
        model: {
          firstName: 'Mark',
          lastName: 'Otto',
          username: '',
          city: '',
          state: '',
          zip: '',
          agree: false
        }
      }
    },
    methods: {
      async onSubmit() {
        // Form submit here
      },
    },
    mounted() {
      this.$refs.formValidator.validate()
    }
  }
</script>
<style>
</style>
