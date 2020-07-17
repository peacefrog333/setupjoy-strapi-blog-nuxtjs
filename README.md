# Setupjoy Strapi Blog NuxtJS (Front end)

See the strapi backend [here](https://github.com/peacefrog333/setupjoy-strapi-blog). This NuxtJS front end would connect to the API generated from the Strapi Backend.

## Structure
Blog content types rendered:\

-- elements\
---- ElementsDivider.vue\
---- ElementsEmbed.vue\
---- ElementsHeaderTitle.vue\
---- ElementsImage.vue\
---- ElementsRangking.vue\
---- ElementsText.vue\

Api endpoint in `nuxt.config.js` file. Change the base URL according to your domain API domain.
```
  api: {
    base: 'http://localhost:1337/',
    blogs: 'blogs',
    blogCategories: 'blog-categories'
  }
```

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

## Deploy on Google AppEngine

```
gcloud app deploy app.yaml --project <project_name>
```



For detailed explanation on how things work on NuxtJS, check out [Nuxt.js docs](https://nuxtjs.org).
