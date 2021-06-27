<template>
  <div class="flex m-auto justify-center text-center items-center h-screen">
    <div class="flex-none w-8 md:w-40"></div>
    <div class="flex-grow">
      <img src="@/assets/imgs/mytigate-logo.svg" class="mb-10" />
      <NuxtLink
        to="/dashboard"
        class="
          border-solid border-2
          rounded-lg
          p-2
          sm:p-3
          text-lg
          sm:text-2xl
          border-blue-400
          text-blue-900
          font-bold
          uppercase
        "
        >Enter our Dashboard</NuxtLink
      >
    </div>
    <div class="flex-none w-8 md:w-40"></div>
  </div>
</template>
