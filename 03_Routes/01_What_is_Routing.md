Routing is determining how the application responds to the request coming from the client. This request comes through a url endpoint and an HTTP method.

![routing diagram](https://i.imgur.com/pN3x62G.png)

A route's syntax looks like this:

```javascript
app.someMethod(routePath, someHandler);
```

- `app` is the instance of our express application.
- `someMethod` represents the HTTP method of the route, such as `get`, `post`, etc.
- `routePath` is the path on the server. It defines the endpoints at which requests can be made.
- `someHandler` is a callback function that will be executed when the client sends a request to this route.

To read more about this topic, [click here](https://expressjs.com/en/starter/basic-routing.html).
