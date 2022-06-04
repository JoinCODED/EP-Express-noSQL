The bigger the application, the harder it is to manage all our routes in the main file `app.js`. To solve this issue, we will create routers that will create a clearer structure of our application.

A router is basically a mini app within our express application, as you can add middleware and routes to it, and load it in the `app` instance. There are no limits to the number of routers in your app.

Let's first move our data to a separate file called `cakeData.js`. Remove the cakes array from `app.js` and move it to `cakeData.js`:

    ```javascript
    const cakes = [
      {
        id: 1,
        name: "Triple Chocolate Cake",
      },
      {
        id: 2,
        name: "Marble Cake",
      },
      {
        id: 3,
        name: "Pumpkin Cake",
      },
    ];

    module.exports = cakes;
    ```

Next step is to create a folder for all routes called `apis`. Inside it create another folder called `cakes`. Inside it create a file called `routes.js`.

Create a `router` instance using the `express.Router` constructor. Then we will create our routes. Keep in mind that those routes are not connected to our express instance `app`, so we will replace `app` with `router`, so now those two routes are a part of this mini app:

In `apis/cakes/routes.js`:

    ```javascript
    const express = require("express");
    const router = express.Router();

    const cakes = require("../cakeData");

    router.get("/", (req, res) => {
      res.json(cakes);
    });

    router.get("/:cakeId", (req, res) => {
      const { cakeId } = req.params;
      const cake = cakes.find((_cake) => _cake.id === +cakeId);
      res.json(cake);
    });

    module.exports = router;
    ```

To load this router in `app.js`, we will require it and call it using `app.use`:

    ```javascript
    const cakeRoutes = require("./api/cakes/routes");

    app.use("/api/cakes", cakeRoutes);
    ```

Now the routes in `cakeRoutes` will only be called if a request's url starts with `/api/cakes`.

To read more about routing, [click here](https://expressjs.com/en/4x/api.html#router).
