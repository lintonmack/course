:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Library

```
As a person,
So I can find multiple books,
I would like to browse books in a library.
```

## Without the Walkthrough

1. Create `Library.test.js`.

2. Write a failing test, and make it pass for the following (finish one before moving onto the next):

```
has no books when instantiated
```

```
can have a book added
```

When writing the code to make the tests pass, focus on small changes, run the tests again and work through the errors - let the tests guide you towards the solution.

***
:bulb:

Hints

A `Library` can have `Book`s, which hints at an array on a `Library` object.

The test for `has no books when instantiated` should expect a getter method on `Library` to return an empty array. See [toHaveLength docs](https://facebook.github.io/jest/docs/expect.html#tohavelengthnumber) on Jest.

The test for `can have a book added` should call a setter method to add a `Book` to the `Library`'s `_books`'s and then assert on a getter method (the same one created to pass the first test) to check the book has been added to the library.
***

## Add, commit and push

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

~~Continue to part 5~~ (coming soon)