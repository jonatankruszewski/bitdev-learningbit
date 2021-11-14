# Using Bit Dev Notes

## Installation

```sh
npx @teambit/bvm install
```

Afterwards installation, added the following environment variable to the .zshrc file:

```sh
echo 'export PATH=$HOME/bin:$PATH' >> ~/.zshrc && source ~/.zshrc
```

## Creating a new workspace

Starting fresh. Harmony is a feature flag.

```sh
bit init --harmony
```

## Install dependencies

```sh
bit install
```

## Create a component

```sh
mkdir components
cd components
mkdir button
cd button
echo 'import React from "react";

const Button = ({ text }) => {
  return <button>{text}</button>;
};

export default Button;
' >> button.tsx

echo 'export * from "./button";' >> index.ts
cd ../../
```

## Add to workspace

```sh
bit add components/button --namespace ui
```

## Show the button

```sh
bit show ui/button
```

Dev files are for tests

## Compiling

```sh
bit compile
```

## Spinning a local dev

```sh
bit start
```

## Creating a composition file

Renders the component in isolation

```sh
echo "import React from "react";
import Button from "./button";

export const BasicButton = () => {
  return <Button text='Hello World'></Button>;
};
" >> ./components/button/button.composition.tsx

```

## Creating documentation

Just create a component.docs.mdx file.
mdx files are md files that can render React.

```sh
echo "
---
name: button
description: a button
labels: ['react', 'button']
---

import Button from './button';

\`\`\`js live
<Button text='Hello World'></Button>
\`\`\`" >> ./components/button/button.docs.mdx
```
