---
gid: 447feed0-0a99-42e2-8354-0df1ffb8808c
title: useCustomer
description: The `useCustomer` hook returns the customer access token of the currently logged in user.
---

The `useCustomer` hook returns an object representing the currently logged in user. It should only be used within server components.

## Example code

{% codeblock file, filename: "App.server.js" %}

```jsx
import {ShopifyProvider, CartProvider, useCustomer} from '@shopify/hydrogen';
import {Suspense} from 'react';

export function App() {
  const {customerAccessToken} = useCustomer();
  return (
    <Suspense fallback="Loading...">
      <ShopifyProvider>
        <CartProvider customerAccessToken={customerAccessToken}>
        ...
      </ShopifyProvider>
    </Suspense>
  );
}
```

{% endcodeblock %}

## Return value

The `useCustomer` hook returns an object with the following keys:

| Key                   | Description                                                                                                                                               |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `customerAccessToken` | The access token of the logged in user. Should be passed as a prop to the [`CartProvider`](https://shopify.dev/api/hydrogen/components/cart/cartprovider) |

If there is no logged in user, an empty object will be returned.

## Related hooks

- [`useCart`](https://shopify.dev/api/hydrogen/hooks/cart/usecart)

## Related Components

- [CartProvider](https://shopify.dev/api/hydrogen/components/cart/cartprovider)