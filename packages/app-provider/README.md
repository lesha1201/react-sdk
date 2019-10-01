# 8base App Provider

Universal 8base App Provider loads fragments schema and provides it to Apollo client, along with authentication and table schema.

# API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Table of Contents

-   [EightBaseAppProvider](#eightbaseappprovider)
    -   [Parameters](#parameters)
    -   [Properties](#properties)

## EightBaseAppProvider

`EightBaseAppProvider` universal provider which loads fragments schema and provides it to Apollo client, along with authentication and table schema.

### Properties

-   `uri` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** The 8base API field schema.
-   `authClient` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** The 8base auth client.
-   `onRequestSuccess` **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)?** Callback which is executed when a request is successful.
-   `onRequestError` **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)?** Callback which is executed when a request fails.
-   `extendLinks` **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)?** Function to extend the standard array of links.
-   `children` **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)?** The render function.

# Usage

```js
import React from 'react';
import { BrowserRouter } from 'react-router-dom';
import { EightBaseAppProvider } from '@8base/app-provider';
import { WebAuth0AuthClient } from '@8base/web-auth0-auth-client';
import { EightBaseBoostProvider, Loader } from '@8base/boost';

import { Routes } from './routes';

const authClient = new WebAuth0AuthClient({
  domain: AUTH_DOMAIN,
  clientId: AUTH_CLIENT_ID,
  redirectUri: `${window.location.origin}/auth/callback`,
  logoutRedirectUri: `${window.location.origin}/auth`,
  workspaceId: 'workspace-id',
});

const Application = () => (
  <BrowserRouter>
    <EightBaseBoostProvider>
      <EightBaseAppProvider uri={ process.env.REACT_APP_8BASE_API_URL } authClient={ authClient }>
        {
          ({ loading }) => loading ? <Loader /> : <Routes />
        }
      </EightBaseAppProvider>
    </EightBaseBoostProvider>
  </BrowserRouter>
);

export { Application };
```