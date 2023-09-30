<script setup>
import router from "../router";
import { useAuth } from "../stores/auth";
// import router from "@/router";
// import { useAuth } from "@/stores/auth.js";
import { ElMessage, ElNotification } from "element-plus";

const auth = useAuth();
function logOut() {
  const success = auth.logout();
  if (success) {
    router.push({ name: "login" });
    ElNotification({
      title: "Success",
      message: "You have Successfully Logged Out",
      type: "success",
      position: "top-right",
      duration: 2000,
    });
  } else {
    ElMessage({
      type: "error",
      message: "Something went wrong",
    });
  }
}
</script>

<template>
  <nav class="bg-teal-400 sticky top-0 shadow-lg">
    <div
      class="flex flex-wrap justify-between items-center mx-auto max-w-screen-xl p-4"
    >
      <RouterLink :to="{ name: 'dashboard' }" class="flex items-center">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M10.5 6h9.75M10.5 6a1.5 1.5 0 11-3 0m3 0a1.5 1.5 0 10-3 0M3.75 6H7.5m3 12h9.75m-9.75 0a1.5 1.5 0 01-3 0m3 0a1.5 1.5 0 00-3 0m-3.75 0H7.5m9-6h3.75m-3.75 0a1.5 1.5 0 01-3 0m3 0a1.5 1.5 0 00-3 0m-9.75 0h9.75"
          />
        </svg>
      </RouterLink>

      <div class="flex items-center">
        <button @click.prevent="logOut()" class="text-lg font-bold text-black">
          Log Out
        </button>
      </div>
    </div>
  </nav>
</template>

<style scoped></style>
