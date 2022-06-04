![Website Architecture](https://i.imgur.com/dFLrWCn.png)
As shown in the diagram above, our backend consists of:

- `Express`: sends and receives data from the frontend.
- `ORM / ODM`: manages and communicates with the database.
- `Database`: saves all of our data.

We can summarize the backend process with the following:

1. `Express` receives a request from the frontend.
2. It passes commands to the `ORM / ODM` which communicates with the database.
3. `Express` sends back a response to the frontend with a status message.
