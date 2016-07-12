---
layout: post
title:  "Today I Learned"
date:   2016-07-11 17:45:00 -0700
categories: node TIL database
---

* You can run `sequelize db:migrate` with an environment flag, `--env=test`, to run your migrations on a second database. I set up a custom `start-test` script to run any pending migrations when I start the test server. This may prove to be time consuming once I start running tests frequently. Another option is to set up a custom `migrate` script to run migrations in development and test at the same time.

* I finally got [a good explanation](https://blog.risingstack.com/node-hero-npm-tutorial/#addingdevelopmentdependencies) of the difference between "dependencies" and "devDependencies" in the `package.json` file. Regular dependencies are packages that the app needs when it's actually running, whether on your local machine or a production server. Development dependencies are only needed in the development environment. For instance, anything related to testing is only necessary in development so it should be included in "devDependencies". Other functions of a development dependency might be minifying and compiling assets before deployment.
