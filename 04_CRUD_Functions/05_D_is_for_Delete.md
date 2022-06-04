Another main method that's used in many applications is the **delete** method. Whether you're removing an item from your cart, or removing a cake from your menu, the logic is the same.

Let's start with analyzing the request and response of a **delete** request:

#### **Request**

1. The HTTP method for a **delete** method should be `DELETE`.
2. The correct naming convention for a URL should start with `/api`, followed by the plural name of the item we're deleting and it should be a noun.
3. Deleting an existing item requires a unique value from the item you want to delete, the most common value sent is the ID. The ID is sent as a route parameter.
4. For example, to delete an existing cake from our list of cakes the route will be `app.delete("/api/cakes/:cakeId")`.

#### **Response**

1. The status code of a successful **delete** request is `204` which simply means `No Content`.
2. By convention, the response body to a **delete** request is empty. We just end the response using `res.end()`.

Let's take a look at what's happening **between** the **request** and **response**:

1. The first step in a **delete** method is to capture the ID from the URL.
2. If the cake exists, it will be deleted by sending the found cake to a function that will delete the cake from the database.
3. By convention, **delete** requests return no content. So the status code is changed to `204` which means `No Content` and the response is ended.
4. If no cake exists with the requested ID, the status is changed to `404` which means `Not Found` and a message is sent as a JSON response.

   ```javascript
   app.delete("/cakes/:cakeId", (req, res) => {
     const { cakeId } = req.params;
     const foundCake = someFunctionThatFetchesAnExistingCake(cakeId);
     if (foundCake) {
       someFunctionThatDeletesAnExistingCake(foundCake);
       res.status(204).end();
     } else {
       res.status(404).json({ message: "Cake not found" });
     }
   });
   ```
