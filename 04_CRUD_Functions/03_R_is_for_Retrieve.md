The main method used in all applications is the retrieve method. There's two main uses for retrieving:

1. **List**: Retrieving an array of objects.
   _(e.g. list of menu items, or list of cart items.)_
2. **Detail**: Retrieving a single object.
   _(e.g. full details of a menu item, or a profile of a single user.)_

**Request**

1. The HTTP method for a retrieve method should be `GET`, as the client is `GET`ting data from the backend.
2. The correct naming convention for a URL should start with `/api`, followed by the plural name of the item we're fetching and it should be a noun. For example, to retrieve a **list** of cakes the route will be `app.get("/api/cakes")`.
3. If you're fetching one specific item, the ID of this item is sent as a route parameter. For example, to retrieve a specific cake the route will be `app.get("/api/cakes/:cakeId")`.

**Response**

1. The returned response is the fetched item, whether it was a list of items or one single item.
2. The status code of a retrieve method is `200` which means that everything is `OK`. It's the default response.

Let's take a look at what's happening **between** the request and response to retrieve a **list**:

1. The **list** of items is fetched from the database and sent back as a JSON response.

   ```javascript
   app.get("/api/cakes", (req, res) => {
     const cakes = someFunctionThatFetchesAllCakes();
     res.json(cakes);
   });
   ```

Now let's take a look at what's happening **between** the request and response to retrieve the **detail**s of a single object:

1. The ID is captured from the URL and passed to a function that will fetch the cake from the database.
2. The returned item is sent as a JSON response.

   ```javascript
   app.get("/api/cakes/:cakeId", (req, res) => {
     const { cakeId } = req.params;
     const cake = someFunctionThatFetchesAnExistingCake(cakeId);
     res.json(cake);
   });
   ```
