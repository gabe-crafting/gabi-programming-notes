---
links: []
title: React cheatsheet
description: ""
---

## React 19

**Actions**: functions that use async transitions are called “Actions”.

### New stuff

- You can now pass a ref as props without forwardRef
- Using actions optimize the rendering process 

### SSR, client side and more

- Added support for server components
- Added support for [metadata](https://react.dev/blog/2024/12/05/react-19#support-for-metadata-tags) in non client apps
- Added string methods for serving html for SSR simpler to optimize NEXT
(`renderToString` and `renderToPipeableStream`)

## Hooks

### useTransition

While function from within is executed, isPending is true.

```tsx
const [isPending, startTransition] = useTransition();

startTransition(async() => { /* some code */ })
```

### useActionState

```tsx
const [error, submitAction, isPending] = useActionState(
  async (previousState, newName) => {
    const error = await updateName(newName);
    if (error) {
      // You can return any result of the action.
      // Here, we return only the error.
      return error;
    }

    // handle success
    return null;
  },
  null,
);

<form action={actionFunction}>
```

### [useFormStatus](https://react.dev/reference/react-dom/hooks/useFormStatus)

status information of the last form submission. For custom submit buttons for example or act on a custom input.

```tsx
const { pending, data, method, action } = useFormStatus();
```

### [useOptimistic](https://react.dev/reference/react/useOptimistic)

useOptimistic is a React Hook that lets you show a different state while an async action is underway.

```tsx
import { useOptimistic } from 'react';

function AppContainer() {
  const [optimisticState, addOptimistic] = useOptimistic(
    state,
    // updateFn
    (currentState, optimisticValue) => {
      // merge and return new state
      // with optimistic value
    }
  );
}
```

### [use](https://react.dev/reference/react/use)

Lets you read the value of a resource like a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) or [context](https://react.dev/learn/passing-data-deeply-with-context).

```tsx
const message = use(messagePromise);
const theme = use(ThemeContext);
```

##

## React libraries

[React helment](https://github.com/nfl/react-helmet) - Library for adding metadata
