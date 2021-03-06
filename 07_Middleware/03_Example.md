A common use for application level middleware is handling requests with non-existing routes.

This middleware is placed after all the routes, right before the `app.listen` method. We place it at the end so that it only gets called if no route matched the request.

```javascript
[...]

app.use((req, res, next) => {
  const err = new Error("Not Found");
  res.status(404);
  res.json({
    error: {
      message: err.message,
    },
  });
});

app.listen(8000, () => {
  [...]
});
```

In the above code, our middleware function creates a new error instance with the message `Not Found` ([read more about it](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)). Then we set the status of the `response` to `404` which means the requested URL doesn't exist.

Finally we pass an error object with a message as a property to the JSON response.
