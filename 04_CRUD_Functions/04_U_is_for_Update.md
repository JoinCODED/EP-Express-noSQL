Another main method that's used in many applications is the **update** method. Whether you're resetting your password, changing your profile image, or increasing the price of your potato cupcakes, the logic is the same.

Let's start with analyzing the request and response of an **update** request:

#### **Request**

1. The HTTP method for an **update** method should be `PUT`.
2. The correct naming convention for a URL should start with `/api`, followed by the plural name of the item we're updating and it should be a noun.
3. Updating an existing item requires a unique value from the item you want to update, the most common value sent is the ID. The ID is sent as a route parameter.
4. For example, to update an existing cake from our list of cakes the route will be `app.put("/api/cakes/:cakeId")`.

#### **Response**

1. The status code of a successful **update** **request** is `200` or `204` which simply means `No Content`.
2. There are two common response contents for updating, sending the updated item using `res.json(updatedCake)`, ending the request the content without returning content using `res.end()`.

Let's take a look at what's happening **between** the **request** and **response**:

1. The first step in an **update** method is to capture the ID from the URL.
2. If the cake exists, it will be updated by sending the found cake and URL's body to a function that will update the cake in the database.
3. We will return the updated cake.
4. If no cake exists with the requested ID, change the status to `404` which means `Not Found` and send a message as a JSON response.

   ```javascript
   app.put("/cakes/:cakeId", (req, res) => {
     const { cakeId } = req.params;
     const foundCake = someFunctionThatFetchesAnExistingCake(cakeId);
     if (foundCake) {
       const updatedCake = someFunctionThatUpdatesAnExistingCake(
         foundCake,
         req.body
       );
       res.json(updatedCake);
     } else {
       res.status(404).json({ message: "Cake not found" });
     }
   });
   ```
