This is what the complete architecture of Express looks like:

![express architecture with controllers](https://i.imgur.com/1UjPfBz.png)

The code in express is split between the routes and controllers. The routes are responsible for receiving requests and sending responses, while controllers are responsible for the functions that the routes call.

So basically, the callback functions in the routes are moved to their own file and called when needed.

Let's create controllers for the following routes:

    ```javascript
    const cakes = require("../cakes");

    router.get("/", (req, res) => {
      res.json(cakes);
    });

    router.get("/:cakeId", (req, res) => {
      const { cakeId } = req.params;
      const cake = cakes.find((_cake) => _cake.id === +cakeId);
      res.json(cake);
    });
    ```

The first step is to create a `controllers.js` file inside `apis/cakes`.

In this file we will save every callback function and export them:

    ```javascript
    const cakes = require("../cakes");

    exports.cakeList = (req, res) => {
      res.json(cakes);
    };

    exports.cakeDetail = (req, res) => {
      const { cakeId } = req.params;
      const cake = cakes.find((_cake) => _cake.id === +cakeId);
      res.json(cake);
    };
    ```

Then, back to your route require `controllers` and pass the functions to their routes:

    ```javascript
    const { cakeList, cakeDetail } = require("./controllers");

    router.get("/", cakeList);

    router.get("/:cakeId", cakeDetail);
    ```

As a result, our code became cleaner and much easier to read.

To read more about controllers, [click here](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/routes).
