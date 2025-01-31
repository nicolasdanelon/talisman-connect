# @talismn/connect

This is the monorepo for the Talisman Connect project.
This project aims to provide the components necessary for Dapp developers to be able to quickly connect to wallets in the Polkadot and Kusama ecosystems.

This turborepo uses [Yarn](https://classic.yarnpkg.com/) as a package manager. It includes the following packages/apps:

#### Install the package:

```
npm i --save @talismn/connect-wallets
```

#### Example
```js
import { getWallets } from '@talismn/connect-wallets';

// get an array of wallets which are installed
const installedWallets = getWallets().filter(wallet => wallet.installed)

// get talisman from the array of installed wallets
const talismanWallet = installedWallets.find(wallet => wallet.extensionName === 'talisman')

// enable the wallet
if (talismanWallet) {
  talismanWallet.enable("myCoolDapp").then(() => {
    talismanWallet.subscribeAccounts((accounts) => {
      // do anything you want with the accounts provided by the wallet
      console.log("got accounts", accounts)
    })
  })
}
```

## Packages

### For Dapps with an existing wallet connection UIs:

- [`@talismn/connect-wallets`](https://github.com/TalismanSociety/talisman-connect/tree/master/packages/connect-wallets)

### For Dapps without an existing wallet connection UI:

- [`@talismn/connect-components`](https://github.com/TalismanSociety/talisman-connect/tree/master/packages/connect-components)

### Generic UIs that can be used for any Dapps:

- [`@talismn/connect-ui`](https://github.com/TalismanSociety/talisman-connect/tree/master/packages/connect-ui)


### Provides interfaces around injected globals for ease of implementation by dapp developers:
- [`@talisman-connect/extension-dapp`](https://github.com/TalismanSociety/talisman-connect/tree/master/packages/extension-dapp)

## Setup

NOTE: We recommend `yarn`

```
cd my-turborepo
yarn run build
```

### Develop

To develop all apps and packages, run the following command:

```
cd my-turborepo
yarn run dev
```

### Remote Caching

Turborepo can use a technique known as [Remote Caching](https://turborepo.org/docs/core-concepts/remote-caching) to share cache artifacts across machines, enabling you to share build caches with your team and CI/CD pipelines.

By default, Turborepo will cache locally. To enable Remote Caching you will need an account with Vercel. If you don't have an account you can [create one](https://vercel.com/signup), then enter the following commands:

```
cd my-turborepo
npx turbo login
```

This will authenticate the Turborepo CLI with your [Vercel account](https://vercel.com/docs/concepts/personal-accounts/overview).

Next, you can link your Turborepo to your Remote Cache by running the following command from the root of your turborepo:

```
npx turbo link
```

## Useful Links

Learn more about the power of Turborepo:

- [Pipelines](https://turborepo.org/docs/core-concepts/pipelines)
- [Caching](https://turborepo.org/docs/core-concepts/caching)
- [Remote Caching](https://turborepo.org/docs/core-concepts/remote-caching)
- [Scoped Tasks](https://turborepo.org/docs/core-concepts/scopes)
- [Configuration Options](https://turborepo.org/docs/reference/configuration)
- [CLI Usage](https://turborepo.org/docs/reference/command-line-reference)
