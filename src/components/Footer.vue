<!--
  This example requires Tailwind CSS v2.0+ 
  
  This example requires some changes to your config:
  
  ```
  // tailwind.config.js
  module.exports = {
    // ...
    plugins: [
      // ...
      require('@tailwindcss/forms'),
    ],
  }
  ```
-->
<template>
  <footer class="bg-white footerthorg dark:bg-gray-800 z-10 relative" aria-labelledby="footer-heading">
    <h2 id="footer-heading" class="sr-only">Footer</h2>
    <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
      <div class="xl:grid xl:grid-cols-3 xl:gap-8">
        <div class="grid grid-cols-2 gap-8 xl:col-span-2">
          <div class="md:grid md:grid-cols-2 md:gap-8">
            <div>
              <h3 class="text-sm font-semibold text-black dark:text-gray-300 golemgradient tracking-wider uppercase">Network</h3>
              <ul role="list" class="mt-4 space-y-4">
                <li v-for="item in navigation.network" :key="item.name">
                  <a
                    :href="item.href"
                    class="text-base text-gray-500 dark:text-gray-400 dark:hover:text-gray-200 thorg-footer-text hover:text-gray-800"
                  >
                    {{ item.name }}
                  </a>
                </li>
              </ul>
            </div>
            <div class="mt-12 md:mt-0">
              <h3 class="text-sm font-semibold text-black dark:text-gray-300 golemgradient tracking-wider uppercase">Provider</h3>
              <ul role="list" class="mt-4 space-y-4">
                <li v-for="item in navigation.provider" :key="item.name">
                  <a
                    :href="item.href"
                    class="text-base text-gray-500 dark:text-gray-400 dark:hover:text-gray-200 thorg-footer-text hover:text-gray-800"
                  >
                    {{ item.name }}
                  </a>
                </li>
              </ul>
            </div>
          </div>
          <div class="md:grid md:grid-cols-2 md:gap-8">
            <div>
              <h3 class="text-sm font-semibold text-black dark:text-gray-300 golemgradient tracking-wider uppercase">Requestor</h3>
              <ul role="list" class="mt-4 space-y-4">
                <li v-for="item in navigation.requestor" :key="item.name">
                  <a
                    :href="item.href"
                    class="text-base text-gray-500 dark:text-gray-400 dark:hover:text-gray-200 thorg-footer-text hover:text-gray-800"
                  >
                    {{ item.name }}
                  </a>
                </li>
              </ul>
            </div>
            <!-- <div class="mt-12 md:mt-0">
              <h3 class="text-sm font-semibold text-black dark:text-gray-300 golemgradient tracking-wider uppercase">Thorg</h3>
              <ul role="list" class="mt-4 space-y-4">
                <li v-for="item in navigation.thorg" :key="item.name">
                  <a
                    :href="item.href"
                    class="text-base text-gray-500 dark:text-gray-400 dark:hover:text-gray-200 thorg-footer-text hover:text-gray-800"
                  >
                    {{ item.name }}
                  </a>
                </li>
              </ul>
            </div> -->
          </div>
        </div>
        <div class="mt-8 xl:mt-0">
          <h3 class="text-sm font-semibold text-black dark:text-gray-300 golemgradient tracking-wider uppercase">Install Golem</h3>
          <p class="mt-4 text-base text-gray-500 dark:text-gray-400 thorg-footer-text">
            Click the button of your interest and let's get started!
          </p>
          <div class="grid grid-cols-2 mt-2">
            <a
              href="https://handbook.golem.network/provider-tutorials/provider-tutorial"
              rel="noreferrer"
              target="_blank"
              class="whitespace-nowrap inline-flex items-center justify-center px-14 py-2 border border-transparent rounded-md shadow-2xl text-base font-medium text-white bg-golemblue hover:bg-blue-600"
            >
              Provider
            </a>
            <a
              href="https://handbook.golem.network/requestor-tutorials/flash-tutorial-of-requestor-development"
              rel="noreferrer"
              target="_blank"
              class="ml-4 whitespace-nowrap inline-flex items-center justify-center px-14 py-2 border border-transparent rounded-md shadow-2xl text-base font-medium text-white bg-golemblue hover:bg-blue-600"
            >
              Requestor
            </a>
          </div>
        </div>
      </div>
      <div class="mt-8 border-t border-gray-700 pt-6 grid grid-cols-12">
        <div class="col-span-12 justify-items-center lg:justify-items-start grid lg:col-span-4 -mt-3">
          <div class="flex items-center">
            <div class="hidden lg:inline h-12 w-12 bg-golemblue rounded-md p-3">
              <component :is="golemicon" class="h-6 w-6 text-white" aria-hidden="true" />
            </div>
            <div class="lg:ml-4">
              <a
                href="https://golem.network"
                rel="noreferrer"
                target="_blank"
                class="text-2xl font-medium text-golemblue golemgradient dark:text-gray-300"
              >
                Golem Network
              </a>
            </div>
          </div>
        </div>
        <div class="lg:col-span-3 col-span-12 justify-items-center grid mt-2 lg:mt-0">
          <p class="text-base text-gray-500 dark:text-gray-400">&copy; 2021 Golem Factory GmbH.</p>
        </div>
        <div class="lg:col-span-4 lg:col-start-9 col-span-12 mt-8 lg:mt-0">
          <div class="grid grid-cols-4 lg:grid-cols-8 gap-6 lg:gap-8 justify-items-center">
            <a
              v-for="item in navigation.social"
              :key="item.name"
              :href="item.href"
              v-bind:class="item.color"
              target="_blank"
              rel="noreferrer"
              class="cursor-pointer col-span-1"
            >
              <span class="sr-only">{{ item.name }}</span>
              <component :is="item.icon" v-bind:class="item.width" class="h-6 w-6 golemblue" aria-hidden="true" />
            </a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import { defineComponent, h } from "vue"
import DiscordIcon from "@/components/discordicon.vue"
import TelegramIcon from "@/components/telegramsvg.vue"
import LinkedinIcon from "@/components/linkedinsvg.vue"
import BlockfolioIcon from "@/components/blockfoliosvg.vue"
import GolemIcon from "@/components/golem.vue"
import { MailIcon } from "@heroicons/vue/outline"

const navigation = {
  network: [
    { name: "Overview", href: "/" },
    { name: "Live Graphs", href: "/network/live" },
    { name: "Historical Statistics", href: "network/historical" },
  ],
  provider: [
    { name: "Online Providers", href: "/network/providers/online" },
    { name: "Node Lookup", href: "/network/providers/lookup/node/" },
    { name: "Nodes by Operator", href: "/network/providers/lookup/operator/" },
    { name: "Pricing Analytics", href: "/network/provider/pricing" },
  ],
  requestor: [{ name: "Overview", href: "/network/requestor" }],
  thorg: [{ name: "Overview", href: "/thorg" }],
  social: [
    {
      name: "GitHub",
      href: "https://github.com/golemfactory",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              "fill-rule": "evenodd",
              d: "M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z",
              "clip-rule": "evenodd",
            }),
          ]),
      }),
      color: "text-black githubicon dark:text-white",
    },
    {
      name: "Twitter",
      href: "https://twitter.com/golemproject",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              d: "M8.29 20.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0022 5.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.072 4.072 0 012.8 9.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 012 18.407a11.616 11.616 0 006.29 1.84",
            }),
          ]),
      }),
      color: "text-twitter",
    },
    {
      name: "Discord",
      href: "https://chat.golem.network",
      icon: DiscordIcon,
    },

    {
      name: "Facebook",
      href: "https://www.facebook.com/golemproject",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              "fill-rule": "evenodd",
              d: "M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z",
              "clip-rule": "evenodd",
            }),
          ]),
      }),
      color: "text-facebook",
    },
    {
      name: "Telegram",
      href: "https://t.me/GolemProject",
      icon: TelegramIcon,
    },
    {
      name: "LinkedIn",
      href: "https://www.linkedin.com/company/golem-network/",
      icon: LinkedinIcon,
      width: "w-14 -ml-3",
    },
    {
      name: "Blockfolio",
      href: "https://blockfolio.com/coin/GLM",
      icon: BlockfolioIcon,
      width: "w-10",
    },
    {
      name: "Mail",
      href: "mailto:contact@golem.network",
      icon: MailIcon,
      color: "text-gray-500 thorgmail dark:text-white",
    },
  ],
}

export default {
  setup() {
    return {
      navigation,
    }
  },
  components: {
    GolemIcon,
  },
  data() {
    return {
      golemicon: "GolemIcon",
    }
  },
}
</script>
