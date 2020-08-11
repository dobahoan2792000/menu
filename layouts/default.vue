/* eslint-disable no-unused-vars */
<template>
  <header class="lg:flex lg:relative lg:box-border lg:px-10 lg:h-20">
    <div
      class="flex py-6 px-10 justify-between border-b leading-3 lg:p-0 lg:border-0"
    >
      <div>
        <button
          type="button"
          class="block text-black hover:text-gray-500 focus:outline-none lg:hidden"
          @click="isOpen = !isOpen"
        >
          <svg class="h-4 w-4 fill-current" viewBox="0 0 24 24">
            <path
              fill-rule="evenodd"
              d="M4 5h16a1 1 0 0 1 0 2H4a1 1 0 1 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2z"
            />
          </svg>
        </button>
      </div>
      <picture
        class="max-w-md h-4 mx-auto lg:absolute lg:top-1/2 lg:v-align lg:ml-8"
      >
        <img src="../img/logo-standard-dark.png" alt="Flowers" class="h-4" />
      </picture>
    </div>
    <nav
      :class="isOpen ? 'block' : 'hidden'"
      class="lg:block lg:ml-20 lg:flex lg:align-middle lg:h-full"
    >
      <ul class="mx-10 lg:flex lg:my-auto lg:h-full">
        <li
          v-for="item in menu"
          :key="item.title"
          :class="item.isExpand ? '' : 'lg:relative'"
          @mouseover="item.isOpen = !item.isOpen"
          @mouseout="item.isOpen = !item.isOpen"
        >
          <a
            :href="item.link"
            class="block font-menu py-3 flex justify-between border-b lg:border-0 lg:items-center lg:py-0 lg:px-6 lg:h-full lg:leading-6 lg:font-mon"
            @click="item.isOpenMobile = !item.isOpenMobile"
            ><span class="lg:line lg:relative">{{ item.title }}</span>
            <svg
              class="inline-block my-auto lg:hidden"
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
              aria-hidden="true"
              focusable="false"
              width="1em"
              height="1em"
              style="
                -ms-transform: rotate(360deg);
                -webkit-transform: rotate(360deg);
                transform: rotate(360deg);
              "
              preserveAspectRatio="xMidYMid meet"
              viewBox="0 0 20 20"
            >
              <path
                d="M9.163 4.516c.418.408 4.502 4.695 4.502 4.695a1.095 1.095 0 0 1 0 1.576s-4.084 4.289-4.502 4.695c-.418.408-1.17.436-1.615 0c-.446-.434-.481-1.041 0-1.574L11.295 10L7.548 6.092c-.481-.533-.446-1.141 0-1.576c.445-.436 1.197-.409 1.615 0z"
                fill="#626262"
              />
            </svg>
          </a>

          <div
            class="lg:absolute lg:left-0 lg:bg-black lg:top-80 lg:transition-height lg:duration-1000 lg:flex lg:items-center"
            :class="[
              item.isExpand ? 'lg:w-screen' : 'lg:w-56',
              item.isOpen
                ? 'lg:py-4 lg: lg:opacity-1 lg:visible'
                : 'lg:h-0 lg:opacity-0 lg:invisible',

            ]"
          >
            <ul
              v-if="item.children && item.children.length"
              :class="[
                item.isExpand
                  ? 'lg:flex-no-wrap lg:flex lg:justify-around w-full'
                  : 'lg:flex-wrap lg:flex lg:pl-10',
              ]"
            >
              <li
              class="dothover"
                v-for="subitem in item.children"
                :key="subitem.title"
                :class="item.isExpand ? '' : 'lg:w-full'"
              >
                <a
                  :href="`${subitem.link}`"
                  class="font-sub-menu font-mon lg:font-bold flex justify-between ml-3 lg:py-1 py-3 border-b lg:border-0 lg:text-white lg:ml-0"
                  :class="item.isExpand ? '' : 'lg:justify-start'"
                  @click="subitem.isOpen = !subitem.isOpen"
                  ><span class="lg:relative lg:dot lg:w-full">
                    <span>{{ subitem.title }}</span>
                  </span>

                  <svg
                    :class="subitem.children ? 'block' : 'hidden'"
                    class="font-menu inline-block my-auto lg:hidden"
                    xmlns="http://www.w3.org/2000/svg"
                    xmlns:xlink="http://www.w3.org/1999/xlink"
                    aria-hidden="true"
                    focusable="false"
                    width="1em"
                    height="1em"
                    style="
                      -ms-transform: rotate(360deg);
                      -webkit-transform: rotate(360deg);
                      transform: rotate(360deg);
                    "
                    preserveAspectRatio="xMidYMid meet"
                    viewBox="0 0 20 20"
                  >
                    <path
                      d="M9.163 4.516c.418.408 4.502 4.695 4.502 4.695a1.095 1.095 0 0 1 0 1.576s-4.084 4.289-4.502 4.695c-.418.408-1.17.436-1.615 0c-.446-.434-.481-1.041 0-1.574L11.295 10L7.548 6.092c-.481-.533-.446-1.141 0-1.576c.445-.436 1.197-.409 1.615 0z"
                      fill="#626262"
                    />
                  </svg>
                </a>
                <ul
                  v-if="subitem.children"
                  :class="subitem.isOpen ? 'block' : 'hidden'"
                  class="lg:block"
                >
                  <li
                    v-for="megaitem in subitem.children"
                    :key="megaitem.title"
                    class=""
                  >
                    <a
                      :href="`${megaitem.link}`"
                      class="font-sub-menu flex justify-between ml-8 py-3 lg:py-2 border-b lg:text-white lg:ml-0 font-mon lg:border-0"
                      >{{ megaitem.title }}
                      <svg
                        :class="megaitem.children ? 'block' : 'hidden'"
                        class="font-menu inline-block my-auto lg:hidden"
                        xmlns="http://www.w3.org/2000/svg"
                        xmlns:xlink="http://www.w3.org/1999/xlink"
                        aria-hidden="true"
                        focusable="false"
                        width="1em"
                        height="1em"
                        style="
                          -ms-transform: rotate(360deg);
                          -webkit-transform: rotate(360deg);
                          transform: rotate(360deg);
                        "
                        preserveAspectRatio="xMidYMid meet"
                        viewBox="0 0 20 20"
                      >
                        <path
                          d="M9.163 4.516c.418.408 4.502 4.695 4.502 4.695a1.095 1.095 0 0 1 0 1.576s-4.084 4.289-4.502 4.695c-.418.408-1.17.436-1.615 0c-.446-.434-.481-1.041 0-1.574L11.295 10L7.548 6.092c-.481-.533-.446-1.141 0-1.576c.445-.436 1.197-.409 1.615 0z"
                          fill="#626262"
                        />
                      </svg>
                    </a>
                  </li>
                </ul>
              </li>
            </ul>
          </div>
        </li>
      </ul>
      <div class="hidden lg:block float-right">
        <div
          class="flex items-center h-full relative cursor-pointer"
          @mouseover="controlDisplayFollow"
          @mouseout="controlDisplayFollow"
        >
          <div>
            <a
              href="#"
              class="lg:font-mon lg:font-menu inline-block lg:leading-6"
            >
              <svg
                class="inline-block"
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
                aria-hidden="true"
                focusable="false"
                width="1em"
                height="1em"
                style="
                  -ms-transform: rotate(360deg);
                  -webkit-transform: rotate(360deg);
                  transform: rotate(360deg);
                "
                preserveAspectRatio="xMidYMid meet"
                viewBox="0 0 20 20"
              >
                <path
                  d="M13.418 7.859a.695.695 0 0 1 .978 0a.68.68 0 0 1 0 .969l-3.908 3.83a.697.697 0 0 1-.979 0l-3.908-3.83a.68.68 0 0 1 0-.969a.695.695 0 0 1 .978 0L10 11l3.418-3.141z"
                  fill="#626262"
                />
              </svg>
              FOLLOW ME
            </a>
            <div
              class="absolute w-56 bg-black left-0 box-content top-80 cursor-default transition-all duration-1000"
              :class="
                isOpenFollow
                  ? 'h-40 visible opacity-1'
                  : 'h-0 invisible opacity-0'
              "
            >
              <div class="p-6">
                <div class="flex justify-center mb-8">
                  <a
                    href="#"
                    class="p-3 border-white-1px flex items-center group hover:bg-white"
                  >
                    <font-awesome-icon
                      :icon="['fab', 'facebook-f']"
                      class="text-white text-xs group-hover:text-black"
                    />
                  </a>

                  <a
                    href="#"
                    class="p-3 border-white-1px flex items-center group hover:bg-white"
                  >
                    <font-awesome-icon
                      :icon="['fab', 'twitter']"
                      class="text-white text-xs group-hover:text-black"
                    />
                  </a>
                  <a
                    href="#"
                    class="p-3 border-white-1px flex items-center group hover:bg-white"
                  >
                    <font-awesome-icon
                      :icon="['fab', 'instagram']"
                      class="text-white text-xs group-hover:text-black"
                    />
                  </a>
                  <a
                    href="#"
                    class="p-3 border-white-1px flex items-center group hover:bg-white"
                  >
                    <font-awesome-icon
                      :icon="['fab', 'pinterest-p']"
                      class="text-white text-xs group-hover:text-black"
                    />
                  </a>
                </div>
                <a href="#" class="text-center block"
                  ><span class="text-white line-w relative tracking-wider"
                    >NEWSLETTER SIGN UP</span
                  ></a
                >
              </div>
            </div>
          </div>
          <svg
            class="mt-1 ml-6 text-black"
            xmlns="http://www.w3.org/2000/svg"
            xmlns:xlink="http://www.w3.org/1999/xlink"
            aria-hidden="true"
            focusable="false"
            width="1em"
            height="1em"
            style="
              -ms-transform: rotate(360deg);
              -webkit-transform: rotate(360deg);
              transform: rotate(360deg);
            "
            preserveAspectRatio="xMidYMid meet"
            viewBox="0 0 20 20"
          >
            <path
              d="M17.545 15.467l-3.779-3.779a6.15 6.15 0 0 0 .898-3.21c0-3.417-2.961-6.377-6.378-6.377A6.185 6.185 0 0 0 2.1 8.287c0 3.416 2.961 6.377 6.377 6.377a6.15 6.15 0 0 0 3.115-.844l3.799 3.801a.953.953 0 0 0 1.346 0l.943-.943c.371-.371.236-.84-.135-1.211zM4.004 8.287a4.282 4.282 0 0 1 4.282-4.283c2.366 0 4.474 2.107 4.474 4.474a4.284 4.284 0 0 1-4.283 4.283c-2.366-.001-4.473-2.109-4.473-4.474z"
              fill="#626262"
            />
          </svg>
        </div>
      </div>
    </nav>
    <Nuxt />
  </header>
</template>
<script>
export default {
  data() {
    return {
      isOpen: false,
      menu: [
        {
          title: 'HOME',
          link: '#',
          isOpen: false,
          isOpenMobile: false,
          isExpand: false,
          height: '270px',
          children: [
            {
              title: 'GALLIANO',
              link: '#',
            },
            {
              title: 'JACOBS',
              link: '#',
            },
            {
              title: 'LAGERFELD',
              link: '#',
            },
            {
              title: 'MCQUEEN',
              link: '#',
            },
            {
              title: 'GAULTIER',
              link: '#',
            },
            {
              title: 'HERRERA',
              link: '#',
            },
            {
              title: 'LANDING',
              link: '#',
            },
          ],
        },
        {
          title: 'FEATURES',
          link: '#',
          isOpen: false,
          isOpenMobile: false,
          isExpand: true,
          height: '394px',
          children: [
            {
              title: 'BLOCKS & SLIDERS',
              link: '#',
              isOpen: false,
              children: [
                {
                  title: 'BLOCK 1',
                  link: '#',
                },
                {
                  title: 'VIDEO BLOCK 1',
                  link: '#',
                },
                {
                  title: 'VIDEO BLOCK 2',
                  link: '#',
                },
                {
                  title: 'POST CAROUSEL 1',
                  link: '#',
                },
                {
                  title: 'POST CAROUSEL 2',
                  link: '#',
                },
                {
                  title: 'POST CAROUSEL 3',
                  link: '#',
                },
                {
                  title: 'POST CAROUSEL 4',
                  link: '#',
                },
                {
                  title: 'POST CAROUSEL 5',
                  link: '#',
                },
              ],
            },
            {
              title: 'POST LAYOUTS',
              link: '#',
              isOpen: false,
              children: [
                {
                  title: 'LAYOUT 1',
                  link: '#',
                },
                {
                  title: 'LAYOUT 2',
                  link: '#',
                },
                {
                  title: 'LAYOUT 3',
                  link: '#',
                },
                {
                  title: 'LAYOUT 4',
                  link: '#',
                },
                {
                  title: 'LAYOUT 5',
                  link: '#',
                },
                {
                  title: 'LAYOUT 6',
                  link: '#',
                },
                {
                  title: 'VIDEO LAYOUT 1',
                  link: '#',
                },
              ],
            },
            {
              title: 'OTHER LAYOUTS',
              link: '#',
              isOpen: false,
              children: [
                {
                  title: 'BLOG MASONRY',
                  link: '#',
                },
                {
                  title: 'STANDARD WITH SIDEBAR',
                  link: '#',
                },
                {
                  title: 'STANDARD WITHOUT SIDEBAR',
                  link: '#',
                },
                {
                  title: 'COMBINED LAYOUT',
                  link: '#',
                },
                {
                  title: 'CATEGORY FILTER',
                  link: '#',
                },
                {
                  title: 'PAGINATION EXAMPLES',
                  link: '#',
                },
              ],
            },
            {
              title: 'POST TYPES',
              link: '#',
              isOpen: false,
              children: [
                {
                  title: 'STANDARD',
                  link: '#',
                },
                {
                  title: 'GALLERY',
                  link: '#',
                },
                {
                  title: 'LINK',
                  link: '#',
                },
                {
                  title: 'QUOTE',
                  link: '#',
                },
                {
                  title: 'AUDIO',
                  link: '#',
                },
                {
                  title: 'VIDEO',
                  link: '#',
                },
              ],
            },
          ],
        },
        {
          title: 'FASHION',
          isOpen: false,
          isOpenMobile: false,
          height: '376px',

          link: '#',
        },
        {
          title: 'PAGES',
          link: '#',
          isOpen: false,
          isOpenMobile: false,
          height: '238px',
          children: [
            {
              title: 'ABOUT US',
              link: '#',
            },
            {
              title: 'MEET THE TEAM',
              link: '#',
            },
            {
              title: 'MY POSTS',
              link: '#',
            },
            {
              title: 'ARCHIVE',
              link: '#',
            },
            {
              title: 'CONTACT US',
              link: '#',
            },
            {
              title: 'TYPOGRAPHY',
              link: '#',
            },
          ],
        },
        {
          title: 'SHOP',
          link: '#',
          isOpen: false,
          isOpenMobile: false,
          height: '206px',
          children: [
            {
              title: 'PRODUCT LIST',
              link: '#',
            },
            {
              title: 'PRODUCT SINGLE',
              link: '#',
            },
            {
              title: 'MY ACCOUNT',
              link: '#',
            },
            {
              title: 'CART',
              link: '#',
            },
            {
              title: 'CHECK OUT',
              link: '#',
            },
          ],
        },
        {
          title: 'NEW',
          isOpen: false,
          isOpenMobile: false,
          link: '#',
          height: '370px',
        },
      ],
      isOpenFollow: false,
    }
  },
  methods: {
    controlDisplayFollow() {
      this.isOpenFollow = !this.isOpenFollow
      return this.isOpenFollow
    },
  },
}
</script>
