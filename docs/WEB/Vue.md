## プロジェクトのキック

- https://docs.volta.sh/guide/getting-started
- https://qiita.com/natsuki3624/items/172525835584093016ad

```
curl https://get.volta.sh | bash
volta install node
volta install pnpm
```

- https://ja.vite.dev/guide/

```
$ pnpm create vuetify

Vuetify.js - Material Component Framework for Vue

✔ Project name: … vuetify-project
✔ Which preset would you like to install? › Recommended (Everything from Default. Adds auto importing, layouts & pinia)
✔ Use TypeScript? … No / Yes
✔ Would you like to install dependencies with yarn, npm, pnpm, or bun? › pnpm
✔ Install Dependencies? … No / Yes

◌ Generating scaffold...
◌ Installing dependencies with pnpm...

Automatically ignored builds during installation:
  esbuild
  unrs-resolver
hint: To allow the execution of build scripts for a package, add its name to "pnpm.onlyBuiltDependencies" in your "package.json", then run "pnpm rebuild".
hint: If you don't want to build a package, add it to the "pnpm.ignoredBuiltDependencies" list.


vuetify-project has been generated at /home/akane/virty/vuetify-project

Discord community: https://community.vuetifyjs.com
Github: https://github.com/vuetifyjs/vuetify
Support Vuetify: https://github.com/sponsors/johnleider
```

## OpenAPI

- https://zenn.dev/ryo034/articles/try-openapi-fetch

```
npm i openapi-fetch
npm i -D openapi-typescript typescript
npx openapi-typescript ./schema.yaml -o ./schema.d.ts
```



## lint周り

- https://qiita.com/yuta-katayama-23/items/a40775326914ee9ed89a

