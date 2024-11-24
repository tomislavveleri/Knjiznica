<template>
  <q-page padding>
    <div class="q-pa-md" style="max-width: 400px">
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
        <q-input
          filled
          v-model="name"
          label="Your name *"
          hint="Name and surname"
          lazy-rules
          :rules="[(val) => (val && val.length > 0) || 'Please type something']"
        />

        <q-input
          filled
          type="number"
          v-model="age"
          label="Your age *"
          lazy-rules
          :rules="[
            (val) => (val !== null && val !== '') || 'Please type your age',
            (val) => (val > 0 && val < 100) || 'Please type a real age',
          ]"
        />
        <q-input
          filled
          v-model="email"
          label="Your email *"
          hint="email"
          lazy-rules
          :rules="[(val) => (val && val.length > 0) || 'Please type something']"
        />
        <q-input
          filled
          v-model="password"
          label="Your password *"
          hint="password"
          type="password"
          lazy-rules
          :rules="[(val) => (val && val.length > 0) || 'Please type something']"
        />

        <div>
          <q-btn label="Submit" type="submit" color="primary" />
          <q-btn
            label="Reset"
            type="reset"
            color="primary"
            flat
            class="q-ml-sm"
          />
        </div>
      </q-form>
    </div>
  </q-page>
</template>

<script>
import { useQuasar } from "quasar";
import { ref } from "vue";
import { useRouter } from "vue-router";

export default {
  setup() {
    const $q = useQuasar();
    const router = useRouter();
    const name = ref(null);

    const age = ref(null);
    const email = ref(null);
    const password = ref(null);

    return {
      name,
      age,
      email,
      password,

      onSubmit() {
        if (name.value && age.value && email.value && password.value) {
          router.push("/");
        } else {
          $q.notify({
            type: "negative",
            message: "Niste unjeli sve podatke", // "You did not enter all the data"
          });
        }
      },

      onReset() {
        name.value = null;
        age.value = null;
        email.value = null;
        password.value = null;
      },
    };
  },
};
</script>
