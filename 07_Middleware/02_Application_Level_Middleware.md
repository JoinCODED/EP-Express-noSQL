Application level middleware is a middleware method that runs every time any request is sent to the application.

To add an application level middleware to your application, we use the `app.use()` method.

Let's take the following example:

```javascript
app.use((req, res, next) => {
  console.log("ONE");
  next();
});
```

The `app.use()` takes a callback function as an argument. This function takes three arguments: the `request` and `response` objects which you can modify them if needed, and the `next` method which is called when the middleware's work is done.

The app will be waiting for `next()` as it signals the end of the middleware function, if you remove it the app will hang because the middleware function is not closed.

After the app runs the the application level middleware method, it will look for the route that has the URL and method that matches the request and send back a response. So, the middleware is just an extra step in between the request and response.

An application can have an endless number of middleware methods. They execute in a sequential order. Let's take the following example:

```javascript
app.use((req, res, next) => {
  console.log("ONE");
  next();
});

app.use((req, res, next) => {
  console.log("TWO");
  next();
});
```

The output of those middleware functions will be:

```shell
ONE
TWO
```

As you can see, `next()` is called at the end of every middleware function to exit the function. But is it the only way to exit a middleware function?

The answer is **no**, it's not the only way. You can also end a middleware function by sending a response.

Basically, the entire app is made of middleware. Example, the url matches the route in this function `app.get("/hello")`, so it will execute this middleware, then a response is sent so the middleware terminates itself. The request/response cycle also ends here, and the response is sent to the client. This process happens with every request that Express receives.
