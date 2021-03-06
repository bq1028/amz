# Apollo GraphQL client/server demo
## Description
The ReactJS app is a demo that allows a user to search for a specific product on amazon.com using the product's ASIN (Amazon Standard Identification Number).

Upon successfully finding the product, the app will present to the user the product's title, sales ranking, and reviews - should it have any. The product information is also saved for future reference.

Under the hood, using both [Apollo's](https://www.apollographql.com/) client and server tools, this app uses [graphql](https://www.graphql.org) queries, mutations, and subscriptions to pull and post data to the data server. The database is then held in an mongodb instance.

## App Workflow
On `http://localhost:3000` the user can input the product ASIN into the search form and hit enter or click on the search button.  

- If the search was successful, then the user will be presented with the details of the product. 
- To demonstrate the use of subscription connections, the reviews of the product will show up on the product details page as they are added
- Another demonstration of the subscription connections are the listing of products on the root page. For example, we have three clients connected to the same data server. Both Client A and B search for different valid ASINs The observer, Client C, should see the products appear on the root page of the application.

Error conditions:

- If the frontend is unable to communicate with the data server it will print a message `Network error: Failed to fetch`
- If the product is in the database, an error modal will be presented to the user indicating so.
- If the product was not found on amazon, an error modal will be presented to the user to try another ASIN

## Requirements
1. MongoDB server running locally
2. Node v9.x

## Setup
The app is organized in two parts: server and client side. Each with their own package requirements and environments.

Build and start server side:

```bash
# Navigate to server side 
cd /path_to_app/server

# using npm 
npm install
# or using yarn
yarn

# to start:
npm run start
# or
yarn start

```

Build and start client side:

```bash
# Navigate to client side 
cd /path_to_app/client

# using npm 
npm install
# or using yarn
yarn

# to start:
npm run start
# or
yarn start
```

Now the user can navigate to `http://localhost:3000` to interact with the app

## Testing
Unit testing is handled by [Jest](https://facebook.github.io/jest). One can find the unit tests in the `src/__tests__` folder within either the client or server directories. 

To run these tests:   
```bash
# server or client side:
npm run test
# or
yarn test
```

In addition we use [Flow](https://flow.org) to type check our components:
```bash
# on the client side only:
npm run flow 
# or 
yarn flow
```

## IDE specifics
[Visual Studio Code](https://code.visualstudio.com/) was used to develop this app. Below are the workspace configurations that will help with automatic eslint'ing:

```javascript
// workspace settings:
{
  // lets vscode ignore type alias and arguments outside of .ts files
  // e.g., without this setting one would get the following: 'type aliases' can only be used in a .ts file.
  "javascript.validate.enable": false,
  // omit the following setting if you want to use npm
  "eslint.packageManager": "yarn", 
  // lets eslint know it these directories have their own eslint configurations
  "eslint.workingDirectories": ["./client", "./server"]
}
```

## Acknowledgments
The following resources helped in the development of this app:

- [Apollo GraphQL Docs](https://www.apollographql.com/docs/react/)
- [How to GraphQL](https://www.howtographql.com/)
- Lynda.com courses:
  * [GraphQL Essential Training](https://www.lynda.com/GraphQL-tutorials/GraphQL-Essential-Training/614315-2.html)
  * [Learning Apollo](https://www.lynda.com/GraphQL-tutorials/Learning-Apollo/614313-2.html)
  * [React Testing and Debugging](https://www.lynda.com/React-js-tutorials/React-Testing-Debugging/592511-2.html)
- [amazon-reviews-crawler](https://github.com/escaladesports/amazon-reviews-crawler) an npm package by [Kennedy Rose](https://github.com/kennedyrose)


## License

Copyright 2018 Fadi Asfour  
Licensed under the [MIT License](LICENSE)
