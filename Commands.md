# Add auth0-lock
## 1. install library
```bash
yarn add auth0-lock
```
## 2. Use Lock
plugins/auth0.js
```js
import Auth0Lock from 'auth0-lock'
import nuxtConfig from '~/nuxt.config'
const config = nuxtConfig.auth0

class Auth0Util {
  showLock(container) {
    const lock = new Auth0Lock(
      config.clientID,
      config.domain,
      {
        container,
        closable: false,
        auth: {
          responseType: 'token id_token',
          redirectUrl: this.getBaseUrl() + '/callback',
          params: {
            scope: 'openid profile email'
          }
        }
      }
    )
    lock.show()
  }

  getBaseUrl() {
    return `${window.location.protocol}//${window.location.host}`
  }
}

export default (context, inject) => {
  inject('auth0', new Auth0Util)
}

```
## 3. Added use of auth0
nuxt.config.js
```js
plugins: [
  '~/plugins/auth0.js'
],
auth0: {
  domain: 'AUTH0_DMAIN',
  clientID: 'AUTH0_CLIENT_ID'
},
```
