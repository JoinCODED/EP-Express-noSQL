![Middleware](https://miro.medium.com/max/679/1*4nJJgPOnlJwD6s-7ygqgTg.jpeg)

Express Middleware are functions that execute during the cycle of a request. In other words, it's a software that sits in the middle of other parts of your application (hence "middle"ware.) It runs after a request is received, but before a response is sent. It has access to both the request and response objects.

You can think of middleware as the time it takes for you to think before answering a question.

Middleware functions can do the following:

- Execute any code.
- Make changes to the request and response objects.
- End the request-response cycle.
- Handle errors.
