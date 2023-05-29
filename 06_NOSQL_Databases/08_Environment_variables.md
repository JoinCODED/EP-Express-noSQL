# Environment Variables.

There is a `Node.js` library called `dotenv` that helps you manage and load environment variables.
But why we should use environment variables?
If the API keys are added to the application, and the code is pushed to a public repository on GitHub, this could lead to an unmonitored access problem. Unknown parties might end up using your API keys, leading to an unintended bill for your cloud services, and other potential security issues.

To solve this problem, the config keys can be added as environment variables and invoked from a closed environment from where the application is deployed.

In `Node.js`, `process.env` is a global variable that is injected during runtime. It is a view of the state of the system environment variables. When we set an environment variable, it is loaded into `process.env` during runtime and can later be accessed.

dotenv is a module available on `npm` to load environment variables into `process.env`. `dotenv` can be added to your `Node.js` project by installing it from `npm`:

```shell
$ npm install dotenv
```

Now, to set the env variables:

1. Create a `.env` file at the root of the project directory.
2. Enter the values you desire, in our case we need to set the `mongoDB` connection string. You should have key-value separated by equal sign.

```shell
DB_HOST = YOUR_CONNECTION_STRING
```

3. Now as early as possible in your application, `app.js` for example, require the `dotenv` module.

```
require('dotenv').config()
```

4. Now back to `database.js`, replace the old plain connection string with our new env variable:

   ```javascript
   const connectDB = async () => {
     const conn = await mongoose.connect(process.env.DB_HOST);
     console.log(`mongo connected: ${conn.connection.host}`);
   };
   ```

5. Finally, add this `.env` file to `.gitignore` so that our credentials are protected.

```shell
# dotenv environment variables file
.env
```

What other values that you may consider adding to your `env` file? your app port, any external api key, your jwt secret and many more.

# Environment Variables in Deployment.

When deploying to services like Netlify or Heroku, environment variables can be set so that our deployed apps can access them.

Using Netlify as an example, open the Netlify Dashboard of the app you’re about to deploy.

Go to Build and Deploy -> Environment Variables.

Now, set the variables and save.

![netlify](https://www.section.io/engineering-education/nodejs-environment-variables/set-vars.png)

Your environment variables are successfully set for deployment on Netlify.
