<script setup>
import Reveal from 'reveal.js';
import Markdown from 'reveal.js/plugin/markdown/markdown.esm.js';
import Highlight from 'reveal.js/plugin/highlight/highlight.esm.js';
import { onMounted } from 'vue'

onMounted(() => {
  Reveal.initialize({
    plugins: [Markdown, Highlight],
    history: true,
    // width: 1200,
    // height: 675,
    margin: 0.1,

    // Bounds for smallest/largest possible scale to apply to content
    // minScale: 0.3,
    // maxScale: 0.7,
  });
})
</script>

<template>
  <div class="reveal">
    <div class="slides">
      <section data-markdown>
      <textarea data-template>
          ## Granular Update to Vue 3 for big projects

          ![](title-schematic.png)
      </textarea>
      </section>

      <section>
        <h2>Who am I & Why You Should Trust Me?</h2>
        <div class="max-w-5xl mx-auto text-white flex items-start gap-12">
          <!-- Profile Image & Contact Info -->
          <div class="flex flex-col items-center text-center">
            <img src="/eugene.jpeg" alt="Eugene" class="w-60 h-60 rounded-full shadow-lg mb-4">

            <div class="space-y-2 text-left text-xs">
              <p>
                ✉️ <span class="font-semibold">Mail:</span>
                <a href="mailto:yauheni.prakopchyk@epicmax.co" class="text-blue-400 hover:text-blue-300 underline">
                  yauheni.prakopchyk@epicmax.co
                </a>
              </p>
              <p>
                🔗 <span class="font-semibold">LinkedIn:</span>
                <a href="https://www.linkedin.com/in/yauheni-prakopchyk" class="text-blue-400 hover:text-blue-300 underline">
                  yauheni-prakopchyk
                </a>
              </p>
            </div>
          </div>

          <!-- About & Experience Section -->
          <div class="flex-1 text-xs">
            <ul class="list-none space-y-3">
              <li>🔥 <span class="font-semibold">10+ years</span> in frontend development</li>
              <li>📌 Worked on <span class="font-semibold">30+ front-end projects</span></li>
              <li>🚀 CTO at <span class="font-semibold">Epicmax</span> (we're laser focused on Vue)</li>
              <li>🛠 Creator & Lead Developer of <span class="font-semibold">Vuestic UI & Vuestic Admin</span></li>
              <li>🔄 Extensive experience transitioning Vue 2 projects</li>
            </ul>
          </div>
        </div>
      </section>

      <section>
        <section data-markdown>
        <textarea data-template>
          ### Agenda

          * What are possible approaches for transition to vue 3? <!-- .element: class="fragment" -->
          * Demo project of transition with module federation and CSS scoping. <!-- .element: class="fragment" -->

          > **Goal:** by the end of presentation - you'll have a powerful tool for project transitioning.
          <!-- .element: class="fragment" -->

          ---

          ### Is my talk important to you?

          * 🤚 Are you still in need of vue 3 transition? <!-- .element: class="fragment" -->
          * 🤚 Is your project too big to transition in one go? <!-- .element: class="fragment" -->
          * 🤘Are you looking for ways to reduce JS technology transition downsides in general? <!-- .element: class="fragment" -->
        </textarea>
        </section>
      </section>

      <section>
        <section>
          <h3>How can you progress with your transition</h3>
          <ul>
            <li class="fragment">Single step transition</li>
            <li class="fragment">Gradual transition with iframes</li>
            <li class="fragment">Gradual transition with module federation and CSS scoping</li>
          </ul>
        </section>

        <section>
          <h3>Single step transition</h3>
          <img class="w-full" src="/single-step-transition.png">
        </section>
        <section>
          <table>
            <tr>
              <th class="bg-red-950/25 text-red-700 !text-center">Cons</th>
              <th class="bg-green-950/25 text-green-500 !text-center">Pros</th>
            </tr>
            <tr>
              <td class="!pt-8 align-top">
                <ul>
                  <li class="fragment" data-fragment-index="1">Takes a while</li>
                  <li class="fragment">Has to be fully completed</li>
                  <li class="fragment">Tough for QA</li>
                </ul>
              </td>
              <td class="!pt-8 align-top">
                <ul>
                  <li class="fragment">Focused development work</li>
                  <li class="fragment">No impact on end users</li>
                </ul>
              </td>
            </tr>
          </table>
          <img class="fragment w-100 justify-self-center fade-in-then-out fragment fixed bottom-5 left-1/2 -translate-x-1/2" data-fragment-index="1" src="/getting-older.gif">
        </section>
        <section>
          <h3>When to use?</h3>
          <ul>
            <li class="fragment">Performance is paramount</li>
            <li class="fragment">You don't need incremental upgrades</li>
          </ul>
        </section>


        <section>
          <h3>Gradual transition with iframes</h3>
          <div class="grid grid-cols-4 gap-4 items-end">
            <img class="fragment" src="/transition-vue2.png" alt="Iframe Transition 1">
            <img class="fragment" src="/iframe-transition-2.png" alt="Iframe Transition 2">
            <img class="fragment" src="/iframe-transition-3.png" alt="Iframe Transition 3">
            <img class="fragment" src="/transition-vue3.png" alt="Iframe Transition 4">
          </div>
        </section>
        <section>
          <table>
            <tr>
              <th class="bg-red-950/25 text-red-700 !text-center">Cons</th>
              <th class="bg-green-950/25 text-green-500 !text-center">Pros</th>
            </tr>
            <tr>
              <td class="!pt-8 align-top">
                <ul>
                  <li class="fragment">Performance overhead from iframes</li>
                  <li class="fragment">Serialized communication</li>
                  <li class="fragment">CORS issues</li>
                </ul>
              </td>
              <td class="!pt-8 align-top">
                <ul>
                  <li class="fragment">Allows incremental upgrades</li>
                  <li class="fragment">No CSS or JS conflicts</li>
                </ul>
              </td>
            </tr>
          </table>
        </section>
        <section>
          <h3>When to use?</h3>
          <ul>
            <li class="fragment">Very important to avoid regressions</li>
            <li class="fragment">Performance is far from your primary concern</li>
          </ul>
        </section>

        <section>
          <h3>Module federation with CSS scoping (SPOILER!)</h3>
          <div class="grid grid-cols-4 gap-4 items-end">
            <img class="fragment" src="/transition-vue2.png" alt="Iframe Transition 1">
            <img class="fragment" src="/federation-transition-2.png" alt="Iframe Transition 2">
            <img class="fragment" src="/federation-transition-3.png" alt="Iframe Transition 3">
            <img class="fragment" src="/transition-vue3.png" alt="Iframe Transition 4">
          </div>
        </section>
        <section>
          <table>
            <tr>
              <th class="bg-red-950/25 text-red-700 !text-center">Cons</th>
              <th class="bg-green-950/25 text-green-500 !text-center">Pros</th>
            </tr>
            <tr>
              <td class="!pt-8 align-top">
                <ul>
                  <li class="fragment">Experimental approach</li>
                  <li class="fragment">Potential for conflicts</li>
                </ul>
              </td>
              <td class="!pt-8 align-top">
                <ul>
                  <li class="fragment">Allows incremental upgrades</li>
                  <li class="fragment">Performance is less of an issue</li>
                </ul>
              </td>
            </tr>
          </table>
        </section>
      </section>
      <section>
        <h3>When to use?</h3>
        <ul>
          <li class="fragment">Performance matters, but doesn't have to be perfect</li>
        </ul>
      </section>

      <section>
        <section>
          <div class="flex flex-col space-y-4 p-4">
            <h3 class="text-xl font-semibold">Example project repo</h3>
            <div class="flex justify-center space-x-4 items-center">
              <img src="/repo.png" alt="Repository Image" class="w-4/5">
              <div class="m-2"/>
              <img src="/repo-qr.png" alt="QR Code for Repo" class="w-1/5">
            </div>
          </div>
        </section>
        <section>
          <div class="flex flex-col space-y-4 p-4">
            <h3 class="text-xl font-semibold">Starting from vue-cli project</h3>
            <div class="flex justify-center space-x-4 items-center">
              <ul class="w-2/3">
                <li>Bootstrap CSS</li>
                <li>Vue CLI</li>
                <li>Vue 2.6</li>
                <li>Vue Router 3</li>
              </ul>
              <div class="m-2"/>
              <img src="/repo-qr.png" alt="QR Code for Repo" class="w-1/3 h-60 w-50">
            </div>
          </div>
        </section>

        <section data-markdown>
        <textarea data-template>

          ### Starting from vue-cli project

          ![](vue2-app.png)

          ---

          ### Project preparation

          * Vue-CLI -> Vite
          * Vue 2.6 -> 2.7
          * Refactor and update

          ---

          ### Create monorepo project

          * pnpm workspaces

          ![](monorepo-structure.png)

          > Optional step, works the same with just 2 repositories.

          ---

          ### Create empty vue 3 project within monorepo

          * Tailwind CSS
          * Vite

          ---

          ![](vue3-project-structure.png)

          ---

          ### Setup module federation

          ![](host-remote.png)

          ---

          ### Add dependencies

          ```js
          // root package.json

          "@originjs/vite-plugin-federation": "^1.3.9",
          ```

          ---

          ### Configure Remote

          ```js
          // vite.config.js

          plugins: [
            vuePlugin(),
            federation({
              name: 'remote-app',
              filename: 'remoteEntry.js',
              exposes: {
                './mainFederation.js': './src/mainFederation.js',
              },
            }),
          ],
          ```

          ---

          ```js
          // mainFederation.js

          export default {
            createVue2App: (selector, routes) => {
              Vue.config.productionTip = false
              Vue.use(Router);

              const router = new Router({
                mode: 'abstract',
                routes,
              });

              new Vue({
                router,
                render: h => h(App),
              }).$mount(selector)

              return router
            },
            routes,
            reactiveState: reactiveState,
          }
          ```

          ---

          ### Configure Host

          ```js
          // vite.config.js

          plugins: [
            vuePlugin(),
            tailwindcss(),
            federation({
              name: 'host-app',
              remotes: {
                remote_app: "http://localhost:5001/assets/remoteEntry.js",
              },
            })
          ],
          ```

          ---

          ### Setup Vue 2 app within Vue 3

          ```html
          <template>
            <div>
              <div id="app-vue2"></div>
            </div>
          </template>

          <script setup>
          import { onMounted } from 'vue'

          import main from 'remote_app/mainFederation.js'

          onMounted(() => {
            routerVue2 = main.createVue2App('#app-vue2')
          })
          </script>
          ```

          ---

          ### Setup Vue 2 app within Vue 3

          ![](vue2-within-vue3-app.png)

          ---

          ### Sync router between vue versions

          ![](router-history-vs-memory.png)

          ---

          ### Sync router between vue versions

          ```js
          let routerVue2
          const routerVue3 = useRouter()

          const areRoutesInSync = () =>
            outerVue3.currentRoute.value.path === routerVue2.currentRoute.path

          const syncVue2Route = () => {
            areRoutesInSync() || routerVue2?.push(routerVue3.currentRoute.value.path)
          }
          const syncVue3Route = () => {
            areRoutesInSync() || routerVue3.push(routerVue2.currentRoute.path)
          }

          onMounted(() => {
            routerVue2 = main.createVue2App('#app-vue2', main.routes)

            syncVue2Route();

            routerVue3.afterEach(syncVue2Route)
            routerVue2?.afterEach(syncVue3Route)
          })
          ```

          ---

          ### CSS Scoping

          ![](autoprefixer-effect.png)

          ---

          ### CSS Scoping

          ```
          // vue2 app package.json

          "autoprefixer": "^10.4.20",
          ```

          ---

          ### CSS Scoping

          ```
          // vue 2 app vite.config.js

          css: {
            postcss: {
              plugins: [
                prefixer({
                  prefix: '#app-vue2',
                  transform(prefix, selector, prefixedSelector, filePath, rule) {
                    const annotation = rule.prev();
                    if (annotation?.type === 'comment' && annotation.text.trim() === 'no-prefix') {
                      return selector; // Do not prefix style rules that are preceded by: /* no-prefix */
                    }

                    return prefixedSelector;
                  },
                }),

                autoprefixer({}) // add options if needed
              ],
            }
          },
          ```
          ---

          ### Migrate pages one by one

          ![](happy-transitioned.png) <!-- .element: class="w-100 fragment" -->

          ---

          [Example app](http://localhost:5000/page1)


        </textarea>
        </section>
      </section>

      <section>
        <section data-markdown>
        <textarea data-template>
          ## Issues with approach

          * Dev Tools
          * Need to support 2 builds for vue 2 app
          * Small performance decrease
          * Data handling

          ---

          ### Dev Tools

          ![](./dev-tools.png)

          > Not shared!

          ---

          ### Need to support 2 builds for vue 2 app

          ![](./two-builds-for-vue2.png) <!-- .element: class="w-160" -->

          ---

          ### Small performance decrease

          * Total amount of JS and CSS is increased

          ![](./double-js-and-css.png) <!-- .element: class="w-100" -->

          ---

          ### Reuse between host and remote

          * Utility functions <!-- .element: class="fragment text-green-500" -->
          * API handling <!-- .element: class="fragment text-green-500" -->
          * Reactive objects <!-- .element: class="fragment text-yellow-500" -->
          * Store <!-- .element: class="fragment text-red-500" -->

          ![](heresy.png)  <!-- .element: class="fragment text-green-500" -->

        </textarea>
        </section>

        <section>
          <h3>CSS Scoping is not perfect</h3>
          <div class="grid grid-cols-2 gap-4">
            <img class="fragment" src="/bootstrap-good.png">
            <img class="fragment" src="/tailwind-no-good.png">
          </div>
        </section>

        <section data-markdown>
        <textarea data-template>
          > It might get better after we get support for **@scope at-rule**:

          ```
          @scope (scope root) to (scope limit) {
            rulesets
          }
          ```

          ![](./scope-at-browser-support.png)

        </textarea>
        </section>
      </section>

<!--      * Storage handling-->
<!--      * Tailwind-->

      <section>
        <section data-markdown>
        <textarea data-template>
          ### Takeaways

          Module federation + CSS scoping offers an effective solution for vue 3 transition.

          ---

          ### Thank you for your attention and time!

          * Contact me:

          ![contact](contact-qr.png)
        </textarea>
        </section>
      </section>
    </div>
  </div>
</template>

<style>
@import url('../node_modules/reveal.js/dist/reveal.css');
@import url('../node_modules/reveal.js/dist/theme/black.css');
@import url('../node_modules/reveal.js/plugin/highlight/monokai.css');

#app {
  width: 100%;
  height: 100%;
}

.reveal {
  font-size: 32px;
}

.reveal blockquote {
  display: block;
  position: relative;
  width: 100%;
  margin: var(--r-block-margin) auto;
  padding: 5px;
  font-style: italic;
  background: rgba(255, 255, 255, 0.05);
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.2);
}

p > img {
  justify-self: center;
}

td, th {
  border: none!important;
}
</style>
