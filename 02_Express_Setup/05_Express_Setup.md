To install `Express` we will use the following command inside our project folder:

  ```shell
    $ npm install express
 ```

To create our `Express` app, we will use the `express` method. This method simply creates an instance of an express application.

In your `app.js`, write the following code:

 ```javascript
    const express = require("express");

    const app = express();
 ```

In the code above, we required the `express` method and called it, it will return an `Express` application which we saved in the constant `app`.

To actually run the application, we need to bind our application to a server, so we will set our development server using the `listen` method. This method is placed at the end of the `app.js` file.

 ```javascript
    app.listen(8000, () => {
      console.log("The application is running on localhost:8000");
    });
  ```

The `listen()` method takes two arguments: the port number which will be 8000, and a callback function -_which is optional_- that we will use to console log the port number in the terminal.

Now, we need to run our Express application, which is `app.js`, and to do that you need to type in the following command in your terminal:

 ```shell
    $ node app.js
 ```

You should now see the following output in the terminal:

 ```shell
    The application is running on localhost:8000
 ```

Lastly, open your browser and go to `localhost:8000`, you'll receive a `404` status and a message saying `Cannot GET /`. This is because we haven't defined a `/` route that sends a response when it's called.

Congratulations! You created your first `Express` app!
