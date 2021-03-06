Route parameters are named URL segments. We use them to capture the values specified at their position in the URL. To create a route parameter in a URL, we add a colon followed with the name of your parameter.

Let's take the following example: We have an array of cake objects, and a request was sent to the following URL: `/cakes/3`. The response to this request is the cake object with the ID 3. The `3` can be any other ID. To access the cake with the ID `3` we will do the following:

  ```javascript
    const cakes = [
      {
        id: 1,
        name: "Triple Chocolate Cake"
      },
      {
        id: 2,
        name: "Marble Cake"
      },
      {
        id: 3,
        name: "Pumpkin Cake"
      }
    ];

    app.get("/cakes/:cakeId", (req, res) => {
      const { cakeId } = req.params;
      const cake = cakes.find(_cake => _cake.id === +cakeId);
      res.json(cake);
    });
  ```

In this case we called our route parameter `cakeId`. So, the value (ID in this case) passed through the URL is saved inside `req.params.cakeId`.

We then compare the `cakeId` value to the IDs in the `cakes` array to fetch the `cake` object with the same ID through the `find` method. Finally we return the found cake as a JSON object.

This is what the response will look like in your browser:
![img](https://i.imgur.com/WpkD0Jk.png)

To read more about routing, [click here](https://expressjs.com/en/guide/routing.html).
