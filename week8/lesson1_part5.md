:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Books should really have names

Before we move onto our interface, it'd be nice if our books had names.

1. Inside `Book.test.js`, modify the `Book` constructor - inside the `beforeEach` callback - so that the first argument is a string, representing the name of the book (and we'll make `chapters` the second argument):

```
book = new Book('Harry Potter', chapters)
```

2. Now write a new test `has a name` and assert that `book.getName()` returns the name you passed into the constructor.

3. Your test should be failing. Write the code to make the test pass and then run your tests. 

**This *might* break your other tests, as the `Book` constructors in the other spec files will now be incorrect (they'll be passed one less argument than they should now be passed). Therefore, keep an eye on the test names in your test runner to make sure this test is actually passing!!**

4. When you are happy you've passed this test, ensure the Book constructors are correct inside your other test files.

## Chapters should also have names

Rinse and repeat!