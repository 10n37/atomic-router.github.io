# Getting Started

## Installation

```bash
npm install effector atomic-router history
```

## View-library bindings

- [**React**](https://github.com/kelin2025/atomic-router-react)
- [**Forest**](https://github.com/sergeysova/atomic-router-forest)
- [**Solid**](https://github.com/Drevoed/atomic-router-solid)

## Initialization

Create your routes wherever you want:

```ts
// @/pages/home
import { createRoute } from 'atomic-router';

export const homeRoute = createRoute();

// @/pages/post
import { createRoute } from 'atomic-router';

export const postRoute = createRoute<{ postId: string }>();
```

And then create a router

```ts
// @/app/routing
import { createHistoryRouter } from 'atomic-router';
import { createBrowserHistory, createMemoryHistory } from 'history';

import { homeRoute } from '@/pages/home';
import { postRoute } from '@/pages/post';

// 1. Define routes
const routes = [
  { path: '/', route: homeRoute },
  { path: '/posts/:postId', route: postRoute },
];

// 2. Create router
const router = createHistoryRouter({
  routes: routes,
});

// 3. Create history
const history = isSsr ? createMemoryHistory() : createBrowserHistory();

// 4. Attach it to router
router.setHistory(history);
```
