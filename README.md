[![herokubtn](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/mmmonica50/mosaico-backend)

- Heroku button page: https://elements.heroku.com/buttons/goodenough/mosaico-backend

[![screencast](https://drive.google.com/uc?export=view&id=0BwQNm5fx5y30SXpSMWI4U1Z3b0E)](https://youtu.be/HqUT2et0FnM)

# Mosaico backend

Ready to go backend for [Mosaico](http://mosaico.io) editor version 0.17.4

Main features are:

- upload templates and images for Mosaico editor
- persist mailings into DB
- an admin manage users/groups
- download ZIP archives of mailings
- sending mailings by email for testing purpose

## Quick start

See the screencast https://youtu.be/sLzZq3cXDi0

## INSTALL

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [ON HEROKU](#on-heroku)
  - [about heroku's stack version](#about-herokus-stack-version)
- [ON ANOTHER SERVER](#on-another-server)
  - [Pre-requisites](#pre-requisites)
  - [Configuration](#configuration)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### ON [HEROKU](https://www.heroku.com/home)

- have an [Heroku account](https://www.heroku.com/home)
- have an [amazon S3 account](https://aws.amazon.com/s3/) for image hosting
- click the heroku deploy button and go through the installation wizard

Heroku uses 2 environment [config vars](https://devcenter.heroku.com/articles/config-vars#setting-up-config-vars-for-a-deployed-application) that will take precedence over our defaults:
![heroku-config-vars](http://imgur.com/download/DAw55D3)

#### about heroku's stack version

This application needs the [cedar-14 stack](https://devcenter.heroku.com/articles/cedar-14-stack) due to some limitations while running [nightmare.js](http://www.nightmarejs.org/)
more informations on [nightmare-heroku](https://github.com/oscarmorrison/nightmare-heroku)

### ON ANOTHER SERVER

#### Pre-requisites

- Node.js >=8.11.4
- [PostgreSQL](https://www.postgresql.org/) >=9.6 ([postgresapp](http://postgresapp.com/) on a mac)
- [Redis](https://redis.io/) (`brew install redis` on mac `redis-server` to start)
- SMTP server (like [mailcatcher](https://mailcatcher.me/): `brew install ruby` – restart terminal – `gem install mailcatcher` then `mailcatcher`)

NB: A compiled version of [sharp](http://sharp.dimens.io/en/stable/) — which is used to resize images and declared as a dependency — should be fetched automatically by npm for your system environment. In case of troubles see [sharp installation instructions](http://sharp.dimens.io/en/stable/install/).

```sh
npm install
npm run dev
```

Then go to: [http://localhost:3000](http://localhost:3000)

#### Configuration

Mosaico backend has a decent localhost-first [default configuration](https://github.com/goodenough/mosaico-backend/blob/master/server/config.js#L13-L53).

We use [rc](https://www.npmjs.com/package/rc) for managing the configuration.
See [rc documentation](https://www.npmjs.com/package/rc#standards) for learning how you can override the default configuration

An easy way to start is by a making a copy of [`.backendrc-example`](https://github.com/goodenough/mosaico-backend/blob/master/.backendrc-example) to a `.backendrc` file and update your configuration here
