The web is a cycle of requests and responses between the clients and servers.

The client sends a `request` to the server which will reply with a `response`.

Let's take an example: Your web browser is the client, and you googled “Coded”. A `request` will be sent to Google’s servers and it will respond with the search results page which is the `response`.

**Requests**

Every request has **a method** and **an endpoint**.

**The endpoint:** is the location of the data in the server that you're making a request to and it's represented as a URL.\
**The method:** is the action that the client is asking the server to do.

The most common **methods** are `GET` and `POST`. Let's take the following examples:

- `GET`: is used to ask the server to give something back, a webpage or some data. It's called `GET` because the client is _`GET`ting_ a resource.\
  _For example, when requesting `joincoded.com` we will receive joincoded`s website._

- `POST`: is used to send data to the server. It's called `POST` because the client is _`POST`ing_ data to the server. \
  _For example, sending the username and password of a user who wants to login to their account._

**Responses**

Every **request** receives a **response**, and every **response** has a _status code_, which represents the status of the **response**. If the **response** is successful, meaning that nothing went wrong in the server, the body of the **response** will be the requested data.

Let's take the following _status codes_:

- `200 OK` : the request was successful
- `404 Not Found` : the requested endpoint does not exist

To read more about this topic, [click here](https://medium.com/@jen_strong/the-request-response-cycle-of-the-web-1b7e206e9047).
