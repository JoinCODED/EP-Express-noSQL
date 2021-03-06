Basically, `Express` **listens** for `requests` that match the `route` and `HTTP method`, and executes their callback function.

Let's take the following example:

  ```javascript
    app.get("/", (req, res) => {
      res.json({ message: "Hello World" });
    });
  ```

This route will handle a `GET` request, and the callback function will be executed when the client requests the path `/` with a `GET` method.

The callback function takes two arguments, the request and response objects.

The response has many methods that send a response back to the client. Those methods terminate the function execution, if no method was called the client request will be hanging forever. This route uses the `res.json()` method to return a `json` object as a response.

To read about other response methods, [click here](https://expressjs.com/en/guide/routing.html#response-methods).
