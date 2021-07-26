## Course follow up repo
https://app.pluralsight.com/library/courses/vue-creating-animations/table-of-contents

Course is based on vue 3 to compare to v2 next chapter on vuejs.org can be used https://vuejs.org/v2/guide/transitions.html.

To apply transitions (animations) we can use existing vue js built in API: transition (https://vuejs.org/v2/api/#transition) and
transition-group (https://vuejs.org/v2/api/#transition-group).

If not specify name property we will get next CSS classes available to do transition (v2 has a bit different set of classes, check docs)
  ```
  .v-enter-from {
    opacity: 0;
    transform: scaleY(0.25);
  }
  .v-enter-to {
    opacity: 1;
    transform: scaleY(1);
  }
  .v-enter-active {
    transition: all .5s ease-in;
  }
  .v-leave-from {
    opacity: 1;
    transform: scaleY(1);
  }
  .v-leave-to {
    opacity: 0;
    transform: scaleY(0.25);
  }
  .v-leave-active {
    transition: all .5s ease-out;
  }
```
If you specified name replace `v-` part with name property value `awesome-`.

To do transitions JavaScript hooks available as well https://vuejs.org/v2/guide/transitions.html#JavaScript-Hooks.

There are good amount of libraries that can provide own API to do transitions. Author showed a few examples with wave-ui
library.

See repo for code examples.

## Up and running

// Install Node.js Latest LTS version
https://nodejs.org/en/

// Install the Vue CLI
// https://cli.vuejs.org/guide/installation.html
npm install -g @vue/cli

// Project setup
npm install

// Compiles and hot-reloads for development
npm run serve

// Compiles and minifies for production
npm run build

// Customize configuration
See: https://cli.vuejs.org/config/

// Wave UI
https://antoniandre.github.io/wave-ui/getting-started

// Wave UI Transitions
https://antoniandre.github.io/wave-ui/transitions