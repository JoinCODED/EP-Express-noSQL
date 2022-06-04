You might've noticed that to see any change that we're making to our code, we need to restart our server. To solve this issue, we will use `nodemon`.

`nodemon` is basically a wrapper for node, it runs node but includes a watch command that watches for changes to the application code and then restarts the server when changes are made.

To install it globally, run the following command in your terminal

    ```bash
    $ npm install -g nodemon
    ```

Instead of running the app using `node`, you will run your app using `nodemon` with the following command inside your project folder:

    ```bash
    $ nodemon app.js
    ```

Your changes are responsive now!
