A very important method that's used in most applications is the **create** method. Whether we're creating a new user, adding an item to a cart, or adding a new item to our menu, the logic is the same.

Let's start with analyzing the request and response of a **create** request:

#### **Request**

1. The HTTP method for a **create** method should be `POST`, because the client is `POST`ing data to the backend.
2. The correct naming convention for a URL should start with `/api`, followed by the plural name of the item we're creating and should be a noun. For example, to add a new cake to our list of cakes the path will be `/api/cakes`.
3. Creating a new item requires the client to send the data in the `body` of the **request**. It can't be in the URL, as it might contain sensitive data (e.g. a new account's password).
4. For example, to add a new cake to our list of cakes the route will be `app.post("/api/cakes")`, and the body can be accessed through `req.body`.

#### **Response**

1. The status code of a successful **create** **request** is `201` which means new data was created.
2. The returned **response** should be the created item, sometimes with new fields added such as the `id` of the item as it's generated in the backend.

Let's take a look at what's happening **between** the **request** and **response**:

1. The body of the request `req.body` is passed to a function.
2. That function **create**s the new item, and adds it to the database.
3. Then returns the new item as a JSON response with status code `201`, which means `Created`.

   ```javascript
   app.post("/cakes", (req, res) => {
     const newCake = someFunctionThatCreatesANewCake(req.body);
     res.status(201).json(newCake);
   });
   ```
