<script setup>
  import axios from "axios";
  import {onMounted, ref} from "vue";

  const shellyParameters = ref("");
  const response = ref("");
  const togglePower = ref("");

  onMounted(async () => {
    const response = await axios.post(
        'https://shelly-86-eu.shelly.cloud/device/status',
        {
          "id": "80646F827174",
          "auth_key": "MWRmYzM2dWlkE62C6C4C76F817CE0A3D2902F5B5D4C115E49B28CF8539114D9246505DE5D368D560D06020A92480"
        },
        {
          headers: {
            'Content-Type': 'application/x-www-form-urlencoded',
          }
        }
    );

    shellyParameters.value = response.data.data.device_status
    console.log(shellyParameters)
  })

  function switchPower () {
    const response = axios.post(
        'https://shelly-86-eu.shelly.cloud/device/status',
        {
          "id": "80646F827174",
          "auth_key": "MWRmYzM2dWlkE62C6C4C76F817CE0A3D2902F5B5D4C115E49B28CF8539114D9246505DE5D368D560D06020A92480"
        },
        {
          headers: {
            'Content-Type': 'application/x-www-form-urlencoded',
          }
        }
    );

    switchPower.value = response.data.data.device_status

  }
</script>

<template>
<p>{{ shellyParameters }}</p>
  <div v-for="(data, key) in shellyParameters">
    <p>{{ key }} : {{ data }}</p>
    <hr>
  </div>

</template>