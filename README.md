# vite-plugin-elm

[![npm](https://img.shields.io/npm/v/vite-plugin-elm.svg?style=for-the-badge)](https://www.npmjs.com/package/vite-plugin-elm)

A plugin enables you to compile an Elm [application](https://package.elm-lang.org/packages/elm/browser/latest/Browser#application)/[document](https://package.elm-lang.org/packages/elm/browser/latest/Browser#document)/[element](https://package.elm-lang.org/packages/elm/browser/latest/Browser#element) on your [vite](https://github.com/vitejs/vite) project. [Hot module replacement](https://vitejs.dev/guide/features.html#hot-module-replacement) works roughly in development.

```ts
import { Elm } from './MyApplication.elm'

Elm.MyApplication.init();
```

## Setup

```
npm i -D vite-plugin-elm
```

Update `vite.config.(js|ts)`

```ts
import elmPlugin from 'vite-plugin-elm'

module.exports = {
  plugins: [elmPlugin()]
}
```

Then you can import `.elm` file like:

```ts
import { Elm } from './Hello.elm'
```

then

```ts
// mount "Hello" Browser.{element,document} on #root
Elm.Hello.init({
  node: document.getElementById('root'),
  flags: "Initial Message"
})
```

See [`/example`](/example) dir to play with an actual vite project. And [this working website](https://github.com/hmsk/hmsk.me) may help you to learn how to use.

## Plugin Options

### `debug` (Default: `process.env.NODE_ENV !== 'production'`)

By giving a boolean, can control debug mode of Elm (means toggle Elm Debugger)

![image](https://user-images.githubusercontent.com/85887/120060168-fd7d8600-c00a-11eb-86cd-4125fe06dc59.png)

```ts
import elmPlugin from 'vite-plugin-elm'

module.exports = {
  plugins: [elmPlugin({ debug: false })]
}
```

When it's `false`, disables debug mode in both development and production. Conversely, enables debug mode even in production by `true`. **When production build gets debug mode, Elm's compile optimization doesn't happen**.

## Acknowledgement

- [klazuka/elm-hot](https://github.com/klazuka/elm-hot) for a helpful referrence of the HMR implementation
- [ChristophP/elm-esm](https://github.com/ChristophP/elm-esm/issues/2) for publishing IIFE -> ESM logic

## License

[MIT](/LICENSE)
