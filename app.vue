<!-- pages/index.vue -->
<template>
  <div>
    <button @click="notify">Notify Me!</button>
  </div>
</template>

<script>
export default {
  methods: {
    notify() {
      if (!("Notification" in window)) {
        alert("This browser does not support desktop notification");
      } else if (Notification.permission === "granted") {
        // If it's okay let's create a notification
        new Notification("Hi there!");
      } else if (Notification.permission !== "denied") {
        // Otherwise, we need to ask the user for permission
        Notification.requestPermission().then(permission => {
          // If the user accepts, let's create a notification
          if (permission === "granted") {
            new Notification("Hi there!");
          }
        });
      }
    }
  }
};
</script>
