![Express Architecture](https://i.imgur.com/Jb1tjbR.png)

How does Express work?
As shown in the diagram above, `Express` does the following:

1. The routes receives a **request** from the frontend.
2. It communicates with the database through `Sequelize` if it needs to _save new data_ to the database or if it wants to _fetch data_ from the database.
3. The routes sends a **response** back to the frontend.

You can learn more about routes and models in later chapters.
