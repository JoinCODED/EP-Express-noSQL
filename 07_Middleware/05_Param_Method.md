One of the common repeated codes is handling route parameters. In most cases, a route parameter has an ID or a unique value, then using this unique value the item is fetched and some logic is applied on it.

So capturing the ID and finding the item is the repeated part of the code.

We will use an express method called `param` that takes two arguments, the name of the route parameter and a callback function. This method will be placed before all the routes in `routes/cakes`.

    ```javascript
    router.param("cakeId", (req, res, next, cakeId) => {});
    ```

This method will ONLY be called before the routes that have a route parameter called `cakeId`.

The callback function takes four arguments: the request and response objects, the [`next`](https://github.com/JoinCODED/Express-Encyclopedia/blob/master/8.%20Middleware/2.%20Application%20Level%20Middleware.md) method, and the captured value from the route parameter `cakeId`.

    ```javascript
    router.param("cakeId", async (req, res, next, cakeId) => {
      const cake = someFunctionThatFetchesAnExistingCake(cakeId);
      if (cake) {
        req.cake = cake;
        next();
      } else {
        const err = someFunctionThatHandlesNotFoundCake();
        next(err);
      }
    });
    ```

Now, we can do whatever we need to with the route parameter. In this case we used it to find a cake. Then, to have the found cake accessible we will save it in the request object. Then we will call `next` to terminate the method and move on to the route that the request was made to.

If the cake was not found, we will creates an error and pass it to the [error-handling middleware](https://github.com/JoinCODED/Express-Encyclopedia/blob/master/8.%20Middleware/4.%20Error%20Middleware.md).

Now the methods that use the route parameter `cakeId` to find a cake can relax and access the found cake from the request object.
