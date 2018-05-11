ember-firebase-service
==============================================================================

Exposes a service that's a direct representation of Firebase.

Installation
------------------------------------------------------------------------------

```
npm install firebase@5.x --save-dev
ember install ember-firebase-service
```

*Versioning will be aligned with Firebase's MAJOR version. For example, if you want to use Firebase v4.x, you would need to depend on the v4.x of this addon.*

### Configuration

Add your Firebase configuration in your app's `config/environment.js`.

```javascript
let ENV = {
  ...

  firebase: {
    apiKey: '<api_key>',
    authDomain: '<auth_domain>',
    databaseURL: '<database_url>',
    projectId: '<project_id>',
    storageBucket: '<storage_bucket>',
    messagingSenderId: '<messaging_sender_id>'
  },

  ...
}
```

Import the Firebase features that you need in your app's `ember-cli-build.js`.

```javascript
'use strict';

const EmberApp = require('ember-cli/lib/broccoli/ember-app');

module.exports = function (defaults) {
  const app = new EmberApp(defaults, {
    ...
  });

  ...

  app.import('node_modules/firebase/firebase-auth.js');
  app.import('node_modules/firebase/firebase-firestore.js');

  return app.toTree();
};
```

> You don't need to import `firebase-app.js` as it's automatically done for you

Usage
------------------------------------------------------------------------------

Inject the `firebase` service and use it as you would use Firebase normally.

```javascript
import { inject } from '@ember/service';
import Component from '@ember/component';

export default Component.extend({
  firebase: inject(),

  init(...args) {
    this._super(...args);

    this.get('firebase').auth().signInWithEmailAndPassword('foo', 'bar');
  }
});
```

Contributing
------------------------------------------------------------------------------

### Installation

* `git clone <repository-url>`
* `cd ember-firebase-service`
* `npm install`

### Linting

* `npm run lint:js`
* `npm run lint:js -- --fix`

### Running tests

* `ember test` – Runs the test suite on the current Ember version
* `ember test --server` – Runs the test suite in "watch mode"
* `ember try:each` – Runs the test suite against multiple Ember versions

### Running the dummy application

* `ember serve`
* Visit the dummy application at [http://localhost:4200](http://localhost:4200).

For more information on using ember-cli, visit [https://ember-cli.com/](https://ember-cli.com/).

License
------------------------------------------------------------------------------

This project is licensed under the [MIT License](LICENSE.md).
