# Intelliada

Cookieless [Intelliada](https://intelliada.com) analytics for any JavaScript app.

Events go straight to Intelliada when you pass a project token. Pass an `endpoint` instead when your server should add the token, which is what [Intelliada for Laravel](https://github.com/ollico/laravel-intelliada) does.

## Install

```bash
npm install intelliada
```

## Usage

```js
import { init } from 'intelliada'

const intelliada = init({
    token: 'your-project-token',
})

intelliada.trackEvent('Signup', { plan: 'pro' })
```

`init` records the current page, then counts later client-side navigations (`history.pushState`, including Inertia, Vue Router, React Router and similar) as pageviews. Set `trackNavigation: false` to keep only the first one. Set `captureExceptions: true` to report uncaught errors.

With a token and no endpoint, events are sent to `https://intelliada.com/api/v1/ingest`. No cookies are set. The visitor hash stays in `sessionStorage` until the tab closes, and automated browsers are ignored.

## Laravel

The Laravel package serves this same client from your own domain and keeps the project token on your server. Install it with Composer rather than using the token in the browser:

```bash
composer require intelliada/laravel
```
