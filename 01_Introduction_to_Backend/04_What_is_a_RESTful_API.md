`REST` stands for **RE**presentational **S**tate **T**ransfer.

It means that when a **RESTful API** is called, the server will **transfer** to the client a **representation** of the **state** of the requested resource. A resource can be a webpage document, a JSON object, or any form of data that the client receives as a response.

What does that mean?

When we call Twitter's API to fetch a specific user (the resource), the API will return **the state** of this user, including their name, number of followers, etc. The state is usually sent in JSON format, which is the format we will be using.

A REST API must provide the server with the following:

- An endpoint: which is the URL from which we will request the resource.
- An HTTP method: which is the action we want to perform on this resource. The most common methods are `GET`, `POST`, `PUT` and `DELETE`.

For example, an API that fetches all cakes from our database will send the server an endpoint and a method. In this case this will be our endpoint (`www.somecakeshop.com/cakes`) and our method will be `GET` which is used to fetch from the server.

> To read more about RESTful APIs, [click here](https://medium.com/extend/what-is-rest-a-simple-explanation-for-beginners-part-1-introduction-b4a072f8740f).
