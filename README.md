# Deploy an Express API to Vercel

## Create a Vercel account

[Sign up for a free Vercel account](https://vercel.com/signup) and give Vercel access to your repository.

## Create an Express API (or use an existing one)

Below and in this repository is a basic example of an API built with Node.js and Express.

```
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(port, () => {
  console.log(`App listening on port ${port}`);
});

module.exports = app;
```

## Export the app

Vercel will convert the Express app into a serverless function. To do this, you need to export the Express API. All it takes is one line of code:

```
module.exports = app;
```

## Create a vercel.json file

Next, create a `vercel.json` file in the root directory of the project. Vercel needs this configuration file to create the Express API and deploy it as a serverless function.

```
{
  "version": 2,
  "builds": [
    {
      "src": "index.js",
      "use": "@now/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/"
    }
  ]
}
```

## Push everything to your repository

## Deploy the app to Vercel

In your Vercel Dashboard, click the **Add new...** button and then select **Project**. Import your repository from GitHub, GitLab or Bitbucket. On the next screen, you can further configure the project (e.g. set environment variables). Finally, click on **Deploy** and you're done.