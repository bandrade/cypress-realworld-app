### Cypress + Report Portal Demo

Forked from this repository [cypress-io/cypress-realworld-app](https://github.com/cypress-io/cypress-realworld-app).

This is a demo used to demonstrate an approach of including test automations in a Software Pipeline. With an increasing number of applications, it is assumed that there are also a lot of automated tests. How to manage the results and create issues in an efficient automated way? One possible solution is to use the Report Portal. This platform uses Elasticsearch, database, UI and Microservices to manage test automation reports, with Machine Learning for analysis and integration with Bug Trackers. A description of its main characteristics and its applicability will be presented through a demo. [Slides in pt-BR](https://speakerdeck.com/_bandrade/incluindo-os-testes-automatizados-no-seu-pipeline-de-forma-eficaz-atraves-do-report-portal)

### Prerequisites

- Have Report Portal [installed](https://reportportal.io/installation)

- Other requirement of this project is to have [Node.js](https://nodejs.org/en/) **version 14** installed on your machine. Refer to the [.node-version](./.node-version) file for the exact version.

- TypeScript will be added as a local dependency to the project, so no need to install it.

- It's needed to change the Report portal url in [Cypress Config files](https://github.com/bandrade/report-portal-cloud-conference-day)


### Installation

```shell
yarn install
```

### Run the app

```shell
yarn dev
```

### Start Cypress

```shell
yarn cypress:open
```

## Tests

| Type | Location                                 |
| ---- | ---------------------------------------- |
| api  | [cypress/tests/api](./cypress/tests/api) |
| ui   | [cypress/tests/ui](./cypress/tests/ui)   |
| unit | [`src/__tests__`](./src/__tests__)       |

## Database

- The local JSON database located in [data/database.json](./data/database.json) and is managed with [lowdb].

- The database is [reseeded](./data/database-seed.json) each time the application is started (via `yarn dev`). Database seeding is done in between each [Cypress End-to-End test](./cypress/tests).

- Updates via the React frontend are sent to the [Express][express] server and handled by a set of [database utilities](backend/database.ts)

- Generate a new database using `yarn db:seed`.

- An [empty database seed](./data/empty-seed.json) is provided along with a script (`yarn start:empty`) to view the application without data.

## Additional NPM Scripts

| Script         | Description                                                                                                                                                                       |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| dev            | Starts backend in watch mode and frontend                                                                                                                                         | |
| start          | Starts backend and frontend                                                                                                                                                       |
| types          | Validates types                                                                                                                                                                   |
| db:seed        | Generates fresh database seeds for json files in /data                                                                                                                            |
| start:empty    | Starts backend, frontend and Cypress with empty database seed                                                                                                                     |
| tsnode         | Customized ts-node command to get around react-scripts restrictions                                                                                                               |
| list:dev:users | Provides id and username for users in the dev database                                                                                                                            |

For a complete list of scripts see [package.json](./package.json)

## Code Coverage Report

The Cypress Real-World App uses the [@cypress/code-coverage](https://github.com/cypress-io/code-coverage) plugin to generate code coverage reports for the app frontend and backend.

To generate a code coverage report:

1. Run `yarn cypress:run --env coverage=true` and wait for the test run to complete.
2. Once the test run is complete, you can view the report at `coverage/index.html`.




