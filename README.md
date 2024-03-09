# What I learned

## Getting Started

### install eleventy

```
cd 11ty-tailwind
### create package.json
npm init -y

### install

npm i -D @11ty/eleventy
```

### verify 11ty working

```
$ npx eleventy
[11ty] Wrote 0 files in 0.01 seconds (v2.0.1)

```

### create first file index.html, and run `npx eleventy`

## install tailwind

tailwind cli

```
npm install -D tailwindcss
npx tailwindcss init
npx tailwindcss -i ./tailwind.css -o ./_site/css/styles.css --watch
```

add in index.html

```
<link rel="stylesheet" href="/css/styles.css" />
```

## dev

```

npx eleventy --serve

### check localhost:8080

```

## config

### Passthrough File Copy

tell 11ty to copy things to "\_site" output folder

create `.eleventy.js` in root folder, and add content

```
module.exports = function (eleventyConfig) {
  // Output directory: _site
  eleventyConfig.addPassthroughCopy("./style.css")
}
```

now create `style.css` under root, this will automatically copied to "\_site", and affect the style of site immediately.

### templating njk

change index.html to index.njk

```
---
layout: "layouts/base.njk"
---

<h1 class="text-4xl font-bold text-blue-500">Hello world!</h1>

```

### layout

create folder "\_includes"
create base layout file "layouts/base.njk"
add html boilplate code here.

```
  <body>
  {{ content | safe }}
  </body>
```

## macro

like react component.
create a file /components/service-macro.njk

```
{% macro service(para1,para2,....) %}
html snippet
{% endmacro %}
```

to use the macro, in /sections/services.njk

```
{% import 'components/service-macro.njk' as macro %}
{{ macro.service('shadow-sm','bg-cyan-400', 'title', 'paragragh') }}
{{ macro.service('shadow-lg','bg-red-400', 'title', 'paragragh') }}
{{ macro.service('shadow-sm','bg-cyan-400', 'title', 'paragragh') }}
```

## deploy

### config

add in package.json

```
  "scripts": {
    "dev": "npx tailwindcss -i ./tailwind.css -o ./_site/css/styles.css --watch",
    "prod": "npx tailwindcss -i ./tailwind.css -o ./_site/css/styles.css"
  },
```

### github

run `git init`

create file `.gitignore`

```
/node_modules
/_site
```

push to github

### create netlify cli

```
npm install -D netlify-cli
npx netlify init
```
