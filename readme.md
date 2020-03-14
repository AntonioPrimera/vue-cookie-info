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

* **text** - (mandatory) The text to be shown in the info box
* **button** - (optional - default: "OK") The label of the button
* **cookie-name** - (optional - default: "cookie-policy-accepted") the name of the cookie to be set when clicking the button in the info box

###Styling

By default the component comes with a specific styling, but if you provide any class to the component, the default styling is removed, so that you can
define your own styling.

e.g. This will have the default styling:

``<cookie-info></cookie-info>``

e.g. Adding a class will remove the default styling and use only the "my-custom-class" styling:

``<cookie-info class="cookie-info-custom-class"></cookie-info>``

You can use this css structure to style the component (in CSS):

```scss
.cookie-info-custom-class{   //from the example above
    //... custom styling of the container
}

.cookie-info-custom-class .vci-text{
    //... custom styling of the text (it's a paragraph)
}

.cookie-info-custom-class .vci-button{
    //... custom styling of the button (it's a simple button element)
}
```

**Remember: if you use custom styling for the container element, you must style the text and the button yourself, the default styling of the text and the button is strictly linked with the default styling of the containing element**