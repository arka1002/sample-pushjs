<template>
  <div>
    <button @click="increment">+1</button>
    <p>{{ counter }}</p>
    <div v-bind:class="styles.cont">
      <button @click="createNotif">Create</button>
      <button @click="closeNotif">Close</button>
    </div>
  </div>
</template>
<script setup>
import Push from "push.js";

const counter = useState("counter", () => 5);

function increment() {
  counter.value++;
}

function createNotif() {
  Push.create("Simple Notif", {
    body: "This is a simple notification.",
    timeout: 5000,
    tag: "foo",
  });
}
function closeNotif() {
  Push.close("foo");
}
</script>

<style module="styles">
.cont {
  display: flex;
  gap: 10px;
  align-items: center;
}
</style>
