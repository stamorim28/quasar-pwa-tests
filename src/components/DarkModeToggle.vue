<template>
  <div>
    <q-toggle
      v-model="darkMode"
      checked-icon="mdi-weather-night"
      color="dark"
      unchecked-icon="mdi-white-balance-sunny"
      size="lg"
    />
  </div>
</template>

<script setup>
import { useQuasar } from "quasar";
import { ref, watch, onMounted } from "vue";

const darkMode = ref(false);
const $q = useQuasar();

watch(darkMode, (darkMode) => {
  $q.dark.set(darkMode);
  $q.localStorage.set("darkMode", darkMode);
});

onMounted(() => {
  const darkModeIsActive = $q.localStorage.getItem("darkMode");

  if (darkModeIsActive) {
    darkMode.value = true;
  }
});
</script>

<style lang="scss" scoped></style>
