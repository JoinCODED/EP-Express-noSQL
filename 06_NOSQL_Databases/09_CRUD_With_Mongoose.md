### General Terminology

**Schemas**: Everything in Mongoose starts with a Schema. Each Schema maps to a MongoDB collection and defines the shape of the documents within that collection. It has information about properties/field types of documents. Schemas can also store information about validation and default values, and whether a particular property is required. In other words, they’re blueprints for documents.

**Model**: A model is a class with which we construct documents.

**Document**: A simple data record.

**Collection**: A set of documents.

**Query**: A request to access data from a database to manipulate it or retrieve it.

After connecting and initializing our database we should define a schema:

### Defining a Schema

Let’s create a schema, `BookSchema` which will have a property name of type String.

```javascript
const Schema = mongoose.Schema;
const BookSchema = new Schema({
  name: String,
});
module.exports = model('Book', BookSchema);
```

This means that the documents defined through this `BookSchema` will have one field, which is a name of type String .

### Creating/Inserting Documents

let’s create a book in our database with the name `Six of crows`

```javascript
let Book = require('../models/Book');
const newBook = Book.create({ name: 'Six of crows' });
```

Beware that all mongoose methods are asynchronous, and should be used with async and await:

```javascript
let Book = require('../models/Book');
const createBook = async () => {
  const newBook = await Book.create({ name: 'Six of crows' });
};
```

### Finding/Reading Documents

To read all documents, we use the `model.find` method without specifying a query. This gives an array of all available documents in the collection.

```javascript
let Book = require('../models/Book');
const getBooks = async () => {
const books = await Book.find();
}
```

To read specifc document we specify the `query` argument in the `model.find` method:

```javascript
let Book = require('../models/Book');
const getBooks = async () => {
  const books = await Book.find(query);
};
```

for example to find all books named as `Six of crows`:

```javascript
let Book = require('../models/Book');
const getBooks = async () => {
  const books = await Book.find({ name: 'Six of crows' });
};
```

### Updating Documents

For updating a document we use `model.updateOne`. As the name suggests, we’ll update the first document that matches the query.

```javascript
let Book = require('../models/Book');
const updateBook = async () => {
  const updatedBook = await Book.updateOne(query, fieldsToUpdate);
};
```

For example to update the book with the name of `Six of crows`:

```javascript
let Book = require('../models/Book');
const updateBook = async () => {
  const updatedBook = await Book.updateOne(
    { name: 'Six of crows' },
    { name: 'Six of crows limited edition' }
  );
};
```

### Deleting Documents

To delete documents, we’ll use either `model.deleteOne` or `model.deleteMany`. Both have similar parameters.

```javascript
let Book = require('../models/Book');
const deleteBook = async () => {
  await Book.deleteOne(query);
};
```

For example to delete the book with the name of `Six of crows`:

```javascript
let Book = require('../models/Book');
const deleteBook = async () => {
  await Book.deleteOne({ name: 'Six of crows' });
};
```
