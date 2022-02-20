# Test case for hashicorp/next-mdx-remote#237
                                             
To reproduce the error:

```shell
yarn install && yarn dev
```

Then visit http://localhost:3000/posts/example-post.

That page should render an example post, but instead you'll get something like:

> Error: Cannot find module '.../next-mdx-remote-237-test-case/node_modules/react/jsx-runtime.js.js' imported from .../next-mdx-remote-237-test-case/node_modules/next-mdx-remote/dist/index.js

If you open `node_modules/next-mdx-remote/dist/index.js` and remove the `.js` from this line:

```js
import * as runtime from 'react/jsx-runtime.js';
```

... the above error clears up, but is replaced by a new one from Preact.
