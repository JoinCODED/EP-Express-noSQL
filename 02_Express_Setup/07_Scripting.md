To run our `express` app, we run the command `nodemon` followed by the name of the file we want to run.

    ```bash
    $ nodemon filename.js
    ```

To run our application using `npm start` we will write a script in our `package.json` we will add a `scripts` **property** which takes an **object** as a value. Every **property** in this **object** is a _script_, the key is the command that will trigger this script and the value is the command we want to execute.

Add the `scripts` property under the last property in your `packeage.json`.

    ```json
    {
      [..],
      "scripts": {
        "start": "nodemon app.js"
      }
    }
    ```

The options are endless with scripting. To read more about it, [click here](https://medium.com/better-programming/write-your-first-shell-script-with-node-js-c612da65b1e1).
