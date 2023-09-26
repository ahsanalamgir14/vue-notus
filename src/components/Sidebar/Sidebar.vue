<template>
  <nav
    class="md:left-0 md:block md:fixed md:top-0 md:bottom-0 md:overflow-y-auto md:flex-row md:flex-nowrap md:overflow-hidden shadow-xl bg-white flex flex-wrap items-center justify-between relative md:w-64 z-10"
  >
    <div
      class="md:flex-col md:items-stretch md:min-h-full md:flex-nowrap px-0 flex flex-wrap items-center justify-between w-full mx-auto"
    >
      <!-- Toggler -->
      <button
        class="cursor-pointer text-black opacity-50 md:hidden px-3 py-1 text-xl leading-none bg-transparent rounded border border-solid border-transparent"
        type="button"
        v-on:click="toggleCollapseShow('bg-white m-2 py-3 px-6')"
      >
        <i class="fas fa-bars"></i>
      </button>
      <!-- Brand -->
      <!-- <router-link
        class="md:block text-left md:pb-2 text-blueGray-600 mr-0 inline-block whitespace-nowrap text-sm uppercase font-bold p-4 px-0"
        to="/"
      >
        Vue Notus
      </router-link> -->

      <header class="header">
        <div class="details">
          <img src="https://images.unsplash.com/photo-1517365830460-955ce3ccd263?ixlib=rb-0.3.5&q=85&fm=jpg&crop=entropy&cs=srgb&ixid=eyJhcHBfaWQiOjE0NTg5fQ&s=b38c22a46932485790a3f52c61fcbe5a" alt="John Doe" class="profile-pic">
          <h1 class="heading">Jane Doe</h1>
          <div class="location">doe@enyata.com</div>
        </div>
      </header>
      <!-- User -->
      <ul class="md:hidden items-center flex flex-wrap list-none px-6">
        <li class="inline-block relative">
          <notification-dropdown />
        </li>
        <li class="inline-block relative">
          <user-dropdown />
        </li>
      </ul>
      <!-- Collapse -->
      <div
        class="md:flex md:flex-col md:items-stretch md:opacity-100 md:relative md:mt-4 md:shadow-none shadow absolute top-0 left-0 right-0 z-40 overflow-y-auto overflow-x-hidden h-auto items-center flex-1 rounded px-6"
        v-bind:class="collapseShow"
      >
        <!-- Collapse header -->
        <div
          class="md:min-w-full md:hidden block pb-4 mb-4 border-b border-solid border-blueGray-200"
        >
          <div class="flex flex-wrap">
            <div class="w-6/12">
              <router-link
                class="md:block text-left md:pb-2 text-blueGray-600 mr-0 inline-block whitespace-nowrap text-sm uppercase font-bold p-4 px-0"
                to="/"
              >
                Vue Notus
              </router-link>
            </div>
            <div class="w-6/12 flex justify-end">
              <button
                type="button"
                class="cursor-pointer text-black opacity-50 md:hidden px-3 py-1 text-xl leading-none bg-transparent rounded border border-solid border-transparent"
                v-on:click="toggleCollapseShow('hidden')"
              >
                <i class="fas fa-times"></i>
              </button>
            </div>
          </div>
        </div>
        <!-- Form -->
        <form class="mt-6 mb-4 md:hidden">
          <div class="mb-3 pt-0">
            <input
              type="text"
              placeholder="Search"
              class="border-0 px-3 py-2 h-12 border border-solid border-blueGray-500 placeholder-blueGray-300 text-blueGray-600 bg-white rounded text-base leading-snug shadow-none outline-none focus:outline-none w-full font-normal"
            />
          </div>
        </form>

        <!-- Divider -->
        <!-- <hr class="my-4 md:min-w-full" /> -->
        <!-- Heading -->
        <!-- <h6
          class="md:min-w-full text-blueGray-500 text-xs uppercase font-bold block pt-1 pb-4 no-underline"
        >
          Admin Layout Pages
        </h6> -->
        <!-- Navigation -->

        <ul class="md:flex-col md:min-w-full flex flex-col list-none">
          <li class="items-center">
            <router-link
              to="/admin/dashboard"
              v-slot="{ href, navigate, isActive }"
            >
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-2 font-bold block"
                :class="[
                  isActive
                    ? 'text-purple-500 hover:text-purple-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="fas fa-meter mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                <div class="flex">
                  <svg width="15" height="13" viewBox="0 0 15 13" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M7.26349 3.24487C7.19309 3.24487 7.13252 3.29462 7.11895 3.36365C6.83815 4.78223 6.36719 7.17656 6.36719 7.27213C6.36719 7.76649 6.76932 8.16882 7.26368 8.16882C7.75805 8.16882 8.16038 7.76669 8.16038 7.27213C8.16038 7.17656 7.68922 4.78223 7.40841 3.36365C7.39445 3.29462 7.33408 3.24487 7.26349 3.24487Z" fill="#2B3C4E"/>
                    <path d="M12.3643 12.2707C12.3724 12.2639 12.3826 12.2609 12.3901 12.253C13.7096 10.8978 14.4362 9.1097 14.4362 7.21799C14.4362 3.23793 11.1982 0 7.21819 0C7.21406 0 7.21012 0.000196535 7.20599 0.000196535C7.20206 0.000196535 7.19813 0 7.194 0C4.4697 0 2.09523 1.52576 0.879782 3.76749C0.319152 4.79318 0 5.96891 0 7.21799C0 9.12307 0.735642 10.9204 2.07144 12.2786C2.11097 12.3187 2.15993 12.3402 2.21086 12.3527C2.2437 12.3649 2.27811 12.372 2.31292 12.372C2.3843 12.372 2.45588 12.3462 2.51251 12.2941L3.28906 11.5805C3.40901 11.4702 3.41687 11.2838 3.30675 11.1636C3.19624 11.0437 3.00982 11.0358 2.89007 11.1461L2.31429 11.6751C1.25812 10.5151 0.655019 9.04009 0.596222 7.47225H1.42625C1.58907 7.47225 1.72122 7.3403 1.72122 7.17728C1.72122 7.01427 1.58907 6.88232 1.42625 6.88232H0.614117C0.659345 5.86056 0.937792 4.89838 1.39833 4.04849C1.68779 3.51913 2.04824 3.0344 2.46532 2.60474L3.04994 3.18936C3.10755 3.24697 3.18306 3.27568 3.25858 3.27568C3.33409 3.27568 3.4096 3.24697 3.46721 3.18936C3.58245 3.07432 3.58245 2.88731 3.46721 2.77228L2.89498 2.20005C3.98124 1.26265 5.37308 0.670357 6.89943 0.597599V1.40915C6.89943 1.57216 7.03157 1.70411 7.19439 1.70411C7.35721 1.70411 7.48936 1.57216 7.48936 1.40915V0.597009C9.05051 0.666227 10.4716 1.28133 11.567 2.25589L10.9827 2.84012C10.8675 2.95516 10.8675 3.14216 10.9827 3.2572C11.0403 3.31482 11.1159 3.34353 11.1914 3.34353C11.2669 3.34353 11.3424 3.31482 11.4 3.2572L11.9897 2.66747C13.0367 3.78007 13.7023 5.2549 13.7745 6.88232H12.9623C12.7995 6.88232 12.6674 7.01427 12.6674 7.17728C12.6674 7.3403 12.7995 7.47225 12.9623 7.47225H13.8403C13.7817 9.02455 13.1893 10.4876 12.1516 11.6429L11.576 11.141C11.4527 11.0337 11.2669 11.0468 11.1597 11.1695C11.0527 11.2922 11.0655 11.4787 11.1882 11.5856L11.9764 12.2731C12.0324 12.3219 12.1014 12.3459 12.1701 12.3459C12.2119 12.3459 12.2534 12.337 12.292 12.3195C12.2945 12.3185 12.2965 12.3164 12.2991 12.3154C12.3225 12.304 12.3439 12.2886 12.3643 12.2707Z" fill="#2B3C4E"/>
                  </svg>
                  <span class="ml-2">
                    Dashboard
                  </span>
                </div>
              </a>
            </router-link>
          </li>

          <li class="items-center">
            <router-link
              to="/admin/assessment"
              v-slot="{ href, navigate, isActive }"
            >
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-2 font-bold block"
                :class="[
                  isActive
                    ? 'text-purple-500 hover:text-purple-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                <div class="flex">
                  <svg width="12" height="16" viewBox="0 0 12 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M10.2316 15.7895H0V0.631579H3.15789V0H8.8421V0.631579H12V14.0211L10.2316 15.7895ZM0.631579 15.1579H9.47368V13.2632H11.3684V1.26316H8.8421V2.21053H3.15789V1.26316H0.631579V15.1579ZM10.1053 13.8947V15.0316L11.2421 13.8947H10.1053ZM3.78947 1.57895H8.21053V0.631579H3.78947V1.57895ZM8.52632 12.3158H5.36842V11.6842H8.52632V12.3158ZM2.87368 12.1579L1.67368 10.9579L2.11579 10.5158L2.81053 11.2105L3.85263 9.91579L4.35789 10.3263L2.87368 12.1579ZM9.78947 10.7368H5.36842V10.1053H9.78947V10.7368ZM9.78947 9.15789H5.36842V8.52632H9.78947V9.15789ZM2.87368 9L1.67368 7.8L2.11579 7.35789L2.81053 8.05263L3.85263 6.75789L4.35789 7.16842L2.87368 9ZM9.78947 7.57895H5.36842V6.94737H9.78947V7.57895ZM9.78947 6H5.36842V5.36842H9.78947V6ZM2.87368 5.8421L1.67368 4.64211L2.11579 4.2L2.81053 4.89474L3.85263 3.6L4.35789 4.01053L2.87368 5.8421ZM9.78947 4.42105H5.36842V3.78947H9.78947V4.42105Z" fill="#2B3C4E"/>
                  </svg>
                  <span class="ml-2">
                    Assessment
                  </span>
                </div>
              </a>
            </router-link>
          </li>

          <li class="items-center">
            <router-link
              to="/auth/login"
              v-slot="{ href, navigate, isActive }"
            >
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-3 font-bold block"
                :class="[
                  isActive
                    ? 'text-purple-500 hover:text-purple-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                 <div class="flex">
                  <svg width="15" height="14" viewBox="0 0 15 14" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M7.98318 8.7738e-05C8.13563 -0.00015831 8.28725 0.0224724 8.43298 0.0672226L12.5752 1.30921C13.0073 1.45504 13.3846 1.72916 13.6569 2.09501C13.9292 2.46085 14.0835 2.90102 14.0991 3.3568L14.0991 10.0702C14.0768 10.5202 13.9195 10.953 13.6477 11.3122C13.3758 11.6715 13.0021 11.9405 12.5752 12.0843L8.43298 13.3598C8.2321 13.4283 8.01784 13.4482 7.80779 13.4178C7.59773 13.3875 7.39786 13.3078 7.22457 13.1853C7.05906 13.0547 6.92662 12.887 6.83798 12.6957C6.74934 12.5044 6.70698 12.295 6.71434 12.0843L6.71434 9.3989C6.71434 9.30987 6.74971 9.22449 6.81266 9.16154C6.87561 9.09859 6.96099 9.06322 7.05002 9.06322C7.13904 9.06322 7.22442 9.09859 7.28737 9.16154C7.35032 9.22449 7.38569 9.30987 7.38569 9.3989L7.38569 12.0843C7.37826 12.1907 7.39631 12.2974 7.43834 12.3955C7.48037 12.4935 7.54517 12.5802 7.62737 12.6482C7.71594 12.7083 7.8176 12.7464 7.92387 12.7592C8.03015 12.7721 8.13795 12.7593 8.23829 12.722L12.3805 11.4801C12.6741 11.3738 12.93 11.1834 13.1163 10.9327C13.3025 10.682 13.4108 10.3821 13.4278 10.0702L13.4278 3.3568C13.4108 3.04496 13.3025 2.745 13.1163 2.49431C12.93 2.24361 12.6741 2.05326 12.3805 1.94698L8.23829 0.704998C8.13908 0.663417 8.03073 0.648469 7.92397 0.661633C7.81721 0.674797 7.71573 0.715616 7.62959 0.780051C7.54346 0.844485 7.47564 0.9303 7.43286 1.029C7.39008 1.1277 7.37382 1.23586 7.38569 1.34277L7.38569 4.02815C7.38569 4.11717 7.35032 4.20255 7.28737 4.2655C7.22442 4.32845 7.13904 4.36382 7.05002 4.36382C6.96099 4.36382 6.87561 4.32845 6.81266 4.2655C6.74971 4.20255 6.71434 4.11717 6.71434 4.02815L6.71434 1.34277C6.70698 1.13208 6.74934 0.922623 6.83798 0.731345C6.92662 0.540068 7.05906 0.372351 7.22457 0.241772C7.44474 0.0814714 7.71086 -0.0033102 7.98318 8.7738e-05Z" fill="#2B3C4E"/>
                    <path d="M1.67919 4.36379C1.74544 4.36512 1.81021 4.38363 1.86716 4.4175C1.9412 4.46796 1.99251 4.54543 2.01008 4.63329C2.02766 4.72114 2.01009 4.81239 1.96115 4.88744L0.739306 6.7135L1.96115 8.53955C2.01101 8.61433 2.02911 8.70585 2.01148 8.79399C1.99386 8.88212 1.94194 8.95964 1.86716 9.00949C1.79238 9.05934 1.70086 9.07745 1.61273 9.05982C1.5246 9.0422 1.44708 8.99028 1.39722 8.9155L0.0545354 6.90147C0.0186651 6.84534 -0.000394821 6.78011 -0.000394821 6.7135C-0.000394821 6.64688 0.0186651 6.58165 0.0545354 6.52552L1.39722 4.51149C1.42915 4.46628 1.47137 4.42932 1.52039 4.40364C1.56942 4.37796 1.62385 4.3643 1.67919 4.36379Z" fill="#2B3C4E"/>
                    <path d="M0.336495 6.37773L12.4207 6.37773C12.5097 6.37773 12.5951 6.41309 12.658 6.47604C12.721 6.539 12.7563 6.62437 12.7563 6.7134C12.7563 6.80243 12.721 6.88781 12.658 6.95076C12.5951 7.01371 12.5097 7.04907 12.4207 7.04907L0.336495 7.04907C0.247469 7.04907 0.162089 7.01371 0.0991392 6.95076C0.0361881 6.88781 0.000823021 6.80243 0.000823021 6.7134C0.000823021 6.62437 0.0361881 6.539 0.0991392 6.47604C0.162089 6.41309 0.247469 6.37773 0.336495 6.37773Z" fill="#2B3C4E"/>
                  </svg>
                  <span class="ml-2">
                    Logout
                  </span>
                </div>
              </a>
            </router-link>
          </li>

          <!-- <li class="items-center">
            <router-link
              to="/admin/settings"
              v-slot="{ href, navigate, isActive }"
            >
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-3 font-bold block"
                :class="[
                  isActive
                    ? 'text-emerald-500 hover:text-emerald-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="fas fa-tools mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                Settings
              </a>
            </router-link>
          </li> -->

          <!-- <li class="items-center">
            <router-link
              to="/admin/tables"
              v-slot="{ href, navigate, isActive }"
            >
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-3 font-bold block"
                :class="[
                  isActive
                    ? 'text-emerald-500 hover:text-emerald-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="fas fa-table mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                Tables
              </a>
            </router-link>
          </li>

          <li class="items-center">
            <router-link to="/admin/maps" v-slot="{ href, navigate, isActive }">
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-3 font-bold block"
                :class="[
                  isActive
                    ? 'text-emerald-500 hover:text-emerald-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="fas fa-map-marked mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                Maps
              </a>
            </router-link>
          </li> -->
        </ul>

        <!-- Divider -->
        <!-- <hr class="my-4 md:min-w-full" /> -->
        <!-- Heading -->
        <!-- <h6
          class="md:min-w-full text-blueGray-500 text-xs uppercase font-bold block pt-1 pb-4 no-underline"
        >
          Auth Layout Pages
        </h6> -->
        <!-- Navigation -->
<!-- 
        <ul class="md:flex-col md:min-w-full flex flex-col list-none md:mb-4">
          <li class="items-center">
            <router-link
              class="text-blueGray-700 hover:text-blueGray-500 text-xs uppercase py-3 font-bold block"
              to="/auth/login"
            >
              <i class="fas fa-fingerprint text-blueGray-300 mr-2 text-sm"></i>
              Login
            </router-link>
          </li>

          <li class="items-center">
            <router-link
              class="text-blueGray-700 hover:text-blueGray-500 text-xs uppercase py-3 font-bold block"
              to="/auth/register"
            >
              <i
                class="fas fa-clipboard-list text-blueGray-300 mr-2 text-sm"
              ></i>
              Register
            </router-link>
          </li>
        </ul> -->

        <!-- Divider -->
        <!-- <hr class="my-4 md:min-w-full" /> -->
        <!-- Heading -->
        <!-- <h6
          class="md:min-w-full text-blueGray-500 text-xs uppercase font-bold block pt-1 pb-4 no-underline"
        >
          No Layout Pages
        </h6> -->
        <!-- Navigation -->

        <!-- <ul class="md:flex-col md:min-w-full flex flex-col list-none md:mb-4">
          <li class="items-center">
            <router-link
              class="text-blueGray-700 hover:text-blueGray-500 text-xs uppercase py-3 font-bold block"
              to="/landing"
            >
              <i class="fas fa-newspaper text-blueGray-300 mr-2 text-sm"></i>
              Landing Page
            </router-link>
          </li>

          <li class="items-center">
            <router-link
              class="text-blueGray-700 hover:text-blueGray-500 text-xs uppercase py-3 font-bold block"
              to="/profile"
            >
              <i class="fas fa-user-circle text-blueGray-300 mr-2 text-sm"></i>
              Profile Page
            </router-link>
          </li>
        </ul> -->

        <!-- Divider -->
        <!-- <hr class="my-4 md:min-w-full" /> -->
        <!-- Heading -->
        <!-- <h6
          class="md:min-w-full text-blueGray-500 text-xs uppercase font-bold block pt-1 pb-4 no-underline"
        >
          Documentation
        </h6> -->
        <!-- Navigation -->
        <!-- <ul class="md:flex-col md:min-w-full flex flex-col list-none md:mb-4">
          <li class="inline-flex">
            <a
              href="https://www.creative-tim.com/learning-lab/tailwind/vue/colors/notus"
              target="_blank"
              class="text-blueGray-700 hover:text-blueGray-500 text-sm block mb-4 no-underline font-semibold"
            >
              <i
                class="fas fa-paint-brush mr-2 text-blueGray-300 text-base"
              ></i>
              Styles
            </a>
          </li>

          <li class="inline-flex">
            <a
              href="https://www.creative-tim.com/learning-lab/tailwind/vue/alerts/notus"
              target="_blank"
              class="text-blueGray-700 hover:text-blueGray-500 text-sm block mb-4 no-underline font-semibold"
            >
              <i class="fab fa-css3-alt mr-2 text-blueGray-300 text-base"></i>
              CSS Components
            </a>
          </li>

          <li class="inline-flex">
            <a
              href="https://www.creative-tim.com/learning-lab/tailwind/angular/overview/notus"
              target="_blank"
              class="text-blueGray-700 hover:text-blueGray-500 text-sm block mb-4 no-underline font-semibold"
            >
              <i class="fab fa-angular mr-2 text-blueGray-300 text-base"></i>
              Angular
            </a>
          </li>

          <li class="inline-flex">
            <a
              href="https://www.creative-tim.com/learning-lab/tailwind/js/overview/notus"
              target="_blank"
              class="text-blueGray-700 hover:text-blueGray-500 text-sm block mb-4 no-underline font-semibold"
            >
              <i class="fab fa-js-square mr-2 text-blueGray-300 text-base"></i>
              Javascript
            </a>
          </li>

          <li class="inline-flex">
            <a
              href="https://www.creative-tim.com/learning-lab/tailwind/nextjs/overview/notus"
              target="_blank"
              class="text-blueGray-700 hover:text-blueGray-500 text-sm block mb-4 no-underline font-semibold"
            >
              <i class="fab fa-react mr-2 text-blueGray-300 text-base"></i>
              NextJS
            </a>
          </li>

          <li class="inline-flex">
            <a
              href="https://www.creative-tim.com/learning-lab/tailwind/react/overview/notus"
              target="_blank"
              class="text-blueGray-700 hover:text-blueGray-500 text-sm block mb-4 no-underline font-semibold"
            >
              <i class="fab fa-react mr-2 text-blueGray-300 text-base"></i>
              React
            </a>
          </li>

          <li class="inline-flex">
            <a
              href="https://www.creative-tim.com/learning-lab/tailwind/svelte/overview/notus"
              target="_blank"
              class="text-blueGray-700 hover:text-blueGray-500 text-sm block mb-4 no-underline font-semibold"
            >
              <i class="fas fa-link mr-2 text-blueGray-300 text-base"></i>
              Svelte
            </a>
          </li>

          <li class="inline-flex">
            <a
              href="https://www.creative-tim.com/learning-lab/tailwind/vue/overview/notus"
              target="_blank"
              class="text-blueGray-700 hover:text-blueGray-500 text-sm block mb-4 no-underline font-semibold"
            >
              <i class="fab fa-vuejs mr-2 text-blueGray-300 text-base"></i>
              VueJS
            </a>
          </li>
        </ul> -->
      </div>
    </div>
  </nav>
</template>
); }

<script>
import NotificationDropdown from "@/components/Dropdowns/NotificationDropdown.vue";
import UserDropdown from "@/components/Dropdowns/UserDropdown.vue";

export default {
  data() {
    return {
      collapseShow: "hidden",
    };
  },
  methods: {
    toggleCollapseShow: function (classes) {
      this.collapseShow = classes;
    },
  },
  components: {
    NotificationDropdown,
    UserDropdown,
  },
};
</script>

<style scoped>

.header {
  min-height: 255px;
  background: #009FFF;
  background: #7557D3;
  color: white;
  clip-path: ellipse(100vw 60vh at 50% 50%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.details {
  text-align: center;
}

.profile-pic {
    height: 80px;
    width: 80px;
    top: 75px;
    -o-object-fit: center;
    border-radius: 50%;
    z-index: 99 !important;
    display: inline !important;
}

.location p {
  display: inline-block;
}

.location svg {
  vertical-align: middle;
}

.stats {
  display: flex;
}

.stats .col-4 {
  width: 10rem;
  text-align: center;
}

.heading {
  font-weight: 400;
  font-size: 1.3rem;
}

</style>