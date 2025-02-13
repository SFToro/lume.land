---
title: Vento
description: Use the Vento template engine to create pages and layouts.
mod: plugins/vento.ts
enabled: false
tags:
  - template_engine
---

## Description

[Vento](https://oscarotero.github.io/vento/) is a template language created by
the same creator as Lume (Óscar Otero) and inspired by other popular template
engines like Nunjucks, Liquid or Eta. This plugin allows you to use it to create
pages and layouts.

## Installation

Import this plugin in your `_config.ts` file to use it:

```js
import lume from "lume/mod.ts";
import vento from "lume/plugins/vento.ts";

const site = lume();

site.use(vento(/* Options */));

export default site;
```

## Creating layouts

Add a file with `.vto` extension in the `_includes` directory. Use the _front
matter_ to set data to the template.

```vento
---
title: Welcome to my page
intro: This is my first post using Lume. I hope you like it!
---

<html>
  <head>
    <title>{{ title }}</title>
  </head>

  <body>
    <p>{{ intro }}</p>
  </body>
</html>
```

## Creating pages

Creating pages is the same as creating layouts; just place the `.vto` file
outside the `_includes` directory.

## vto filter

The Vento plugin also registers the `vto` filter, to render any string value as
a Vento template and output it as HTML. The filter accepts an object with data.
For example, to render Vento code inside a Nunjucks template:

```html
---
data:
  username: Oscar
text: "Hello {{ username }}"
---

<!-- Render a string -->
<div>{{ text | vto(data) | safe }}<div>
```

## Configure VSCode

You can use the
[Vento extension for VS Code](https://marketplace.visualstudio.com/items?itemName=oscarotero.vento-syntax)
for syntax highlight and some useful snippets.
