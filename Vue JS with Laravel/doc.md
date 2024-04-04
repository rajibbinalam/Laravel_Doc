## Vue 3 with Laravel
#### Install in a laravel project
```sh
npm install vue@3 vue-loader@next vue-router@next --force

npm install @vitejs/plugin-vue --force --save-dev 
```

#### Config -> vite.config.js
```js
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';
import vue from '@vitejs/plugin-vue';            // New Added

export default defineConfig({
    plugins: [
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
        vue(),                                  // New Added
    ],
});
```
#### Main Vue App File: resources->js->app.js
```js
import './bootstrap';
import {createApp} from 'vue'

import app from './components/app.vue'          // rndering vue File

createApp(app).mount('#app')
```
