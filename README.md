# GRANDstack temp versie

Hierbij mijn versie van GRANDstack. Hierbij heb ik met mock data gewerkt en geprobeerd een skeleton te maken voor toekomstige doeleinden.

Orgineel: <https://github.com/grand-stack/grand-stack-starter>

##### Binnen GRANDstack wordt er gebruik gemaakt van 4 lagen
- GraphQL: geschikt voor het ontwikkelen van API's en bevat de schema's.
- React: UI ontwikkeld vanuit een Js library
- Apollo: Server en Client, tool om met GraphQL te werken
- Neo4j: Native graph database gebasseerd op een property datamodel

Alles in het Engels is van het orgineel overgenomen, wellicht wordt dit in de toekomst vervangen.

Zodra de sandbox is ingesteld, hoort alles het te doen mits alles hieronder succesvol wordt uitgevoerd.

## Quick start
For schemas using the  `@cypher` directive (as in this repo) via [`neo4j-graphql-js`](https://github.com/neo4j-graphql/neo4j-graphql-js), you need to have the [APOC library](https://github.com/neo4j-contrib/neo4j-apoc-procedures) installed, which should be automatic in Sandbox, Cloud and is a single click install in Neo4j Desktop. If when using the Sandbox / cloud you encounter an issue where an error similar to `Can not be converted to long: org.neo4j.kernel.impl.core.NodeProxy, Location: [object Object], Path: users` appears in the console when running the React app, try installing and using Neo4j locally instead.

Uitleg via video: https://www.youtube.com/watch?v=rPC71lUhK_I

#### Sandbox setup
TODO: Sandbox step-to-step uitleg toevoegen.

Op dit moment draait hij om op mijn eigen sandbox, mocht er een persoonlijke sandbox worden gebruikt moeten de volgende variabelen vervangen worden:
Via <https://sandbox.neo4j.com/> moet er eerst met een Neo4j account worden ingelogd (gratis). Vervolgens, zodra er een "Blank Sandbox" is aangemaakt en runned, kunnen we beginnen met het vervangen van een aantal variabelen.

- in ./api/.env staan er een aantal velden.
- Vervang NEO4J_URI en NEO4J_PASSWORD voor de desbetreffende velden binnen je eigen sandbox details.


### [`/api`](./api)

*Install dependencies*

```
(cd ./ui-react && npm install)
(cd ./ui-angular && npm install)
(cd ./api && npm install)
```

*Start API server*
```
cd ./api && npm start
```

![](api/img/graphql-playground.png)

### [`/ui-react`](./ui-react)

This will start the GraphQL API in the foreground, so in another terminal session start the React UI development server:

*Start the React UI server*
```
cd ./ui-react && npm start
```

![](ui-react/img/default-app.png)

### [`/ui-angular`](./ui-angular)

A UI built with [Angular](https://angular.io), [Apollo](https://www.apollographql.com/docs/angular/) and the [Clarity Design System](https://clarity.design) is also available.

*Start the Angular UI server*
```
cd ./ui-angular && npm start
```

![](ui-angular/img/angular-ui.jpg)

See [the project releases](https://github.com/grand-stack/grand-stack-starter/releases) for the changelog.

## Deployment

### Zeit Now v2

TODO: Zeit now werkende krijgen zodat de toekomstige website niet alleen lokaal geopend kan worden. Op dit moment echter nog problemen hiermee.

Zeit Now v2 can be used with monorepos such as grand-stack-starter. [`now.json`](https://github.com/grand-stack/grand-stack-starter/blob/master/now.json) defines the configuration for deploying with Zeit Now v2.

1. Set the now secrets for your Neo4j instance:

```
now secret add NEO4J_URI bolt+routing://<YOUR_NEO4J_INSTANCE_HERE>
now secret add NEO4J_USER <YOUR_DATABASE_USERNAME_HERE>
now secret add NEO4J_PASSWORD <YOUR_DATABASE_USER_PASSWORD_HERE>
```

2. Run `now`

### Zeit Now v1

1. Run `now` in `/api` and choose `package.json` when prompted.
1. Set `REACT_APP_GRAPHQL_API` based on the API deployment URL from step 1 in `ui-react/.env`
1. Run `now` in `/env` and choose `package.json` when prompted.

## Docker Compose

You can quickly start via:
```
docker-compose up -d
```

Dit moet als het goed is ook werken, heb de docker-compose.yml aangepast op de instellingen van mijn sandbox.


This project is licensed under the Apache License v2.
Copyright (c) 2018 Neo4j, Inc.
