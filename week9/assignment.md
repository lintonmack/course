## Assignment

The assignment for this week is to use Express and MongoDB to create a guest book.

The guest book should have multiple inputs: a `person` text input, and a `comment` text input. When a person leaves a comment, their name and comment should appear on the page (and should persist on refresh).

You should be able to delete comments.

### Bonus points
* Store the [current date](https://stackoverflow.com/questions/1531093/how-do-i-get-the-current-date-in-javascript) on each document in a `createdAt` field.
* [Sort the comments on the page by date in descending order](http://mongoosejs.com/docs/api.html#query_Query-sort) (newest first).