<template>
  <q-page padding>
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
        v-model="password"
        label="Your password *"
        hint="password"
        type="password"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Please type something']"
      />
      <div>
        <q-btn label="Submit" type="submit" color="primary" />
      </div>
    </q-form>
    <!-- content -->
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

    const password = ref(null);

    return {
      name,

      password,

      onSubmit() {
        if (name.value && password.value) {
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

        password.value = null;
      },
    };
  },
};
</script>
