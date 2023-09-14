This is a [Next.js](https://nextjs.org/) template to use when reporting a [bug in the Next.js repository](https://github.com/vercel/next.js/issues) with the `app/` directory.

## Getting started

Run `yarn` to install all necessary packages.

## Description of the bug

It seems like the `-H` (hostname) flag is not respect when spinning up the dev server.

Running the following command `next dev -p 4567 -H local.my-domain.com` will still cause Next.js to serve the page from `127.0.0.1:4567`` instead of the expected `local.my-domain.com:4567``:

```
yarn run v1.22.19
$ next dev -p 4567 -H local.my-domain.com
  ▲ Next.js 13.4.20-canary.28
  - Local:        http://127.0.0.1:4567
  - Network:      127.0.0.1:4567

 ✓ Ready in 2.6s
```

The `package.json` has been updated so you can reproduce this by running `yarn dev`. I have verified that `local.my-domain.com` has been added to the `/etc/hosts` file. This used to work on earlier versions of next, but seems to be broken in the latest canary.