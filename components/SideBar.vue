<template>
  <div class="bg-blue-900 sm:w-1/4 lg:w-1/6 shadow-2xl p-5">
    <div>
      <nuxt-link to="/">
        <img
          src="@/assets/imgs/mytigate-logo-negative.png"
          class="m-0 sm:m-auto inline-block sm:block"
        />
      </nuxt-link>
      <svg
        style="width: 24px; height: 24px"
        viewBox="0 0 24 24"
        class="sm:hidden inline-block float-right"
        @click="toggle = !toggle"
      >
        <path fill="#fff" d="M3,6H21V8H3V6M3,11H21V13H3V11M3,16H21V18H3V16Z" />
      </svg>
    </div>
    <div class="mt-4 sm:mt-8 sm:block" :class="{ hidden: toggle }">
      <ul class="list-none text-white">
        <li class="mb-3">
          <svg
            class="inline-block align-text-bottom"
            style="width: 24px; height: 24px"
            viewBox="0 0 24 24"
          >
            <path fill="#fff" d="M10,20V14H14V20H19V12H22L12,3L2,12H5V20H10Z" />
          </svg>
          <nuxt-link to="/" class="pl-2">Home</nuxt-link>
        </li>
        <li class="mb-3">
          <svg
            class="inline-block align-text-bottom"
            style="width: 24px; height: 24px"
            viewBox="0 0 24 24"
          >
            <path
              fill="#fff"
              d="M9,2V8H11V11H5C3.89,11 3,11.89 3,13V16H1V22H7V16H5V13H11V16H9V22H15V16H13V13H19V16H17V22H23V16H21V13C21,11.89 20.11,11 19,11H13V8H15V2H9Z"
            />
          </svg>
          <nuxt-link to="#" class="pl-2">Dashboard</nuxt-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SideBar',
  data() {
    return {
      toggle: true,
    }
  },
}
</script>
