#A Basic Cookie Usage Info Component

Shows a simple information box on the bottom of the page, with a given text (usually stating that the current website uses cookies) and displays a button (usually an "OK" button).

As long as the user doesn't click the button, the info box will be displayed every time the page loads / refreshes.

When the user clicks the button, a cookie is set and the info box is not displayed anymore.

Use this component for basic GDPR compliance.

At the moment, this component has hardcoded styling. In future versions, the styling might be customizable.

This component is served as a single file vue component and is not built. You need a compiler / builder to consume SFCs.

##Install

``$ npm install vue-cookie-info``

or

``$ yarn add vue-cookie-info``

##Usage

**In a Vue file:**

```javascript
import VueCookieInfo from 'vue-cookie-info';

export default {
	components: {
        'cookie-info': VueCookieInfo,
	},

    //...
}
```

**In a js file (like Laravel's app.js):**

```javascript
window.Vue = require('vue');

Vue.component('cookie-info', require('./components/CookieInfo').default);

const app = new Vue({
    el: '#app',
});
```

###Parameters
