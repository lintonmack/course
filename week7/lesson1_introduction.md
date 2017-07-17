## Introduction

We are going to create a cruise ship application. It will be built solely for the purpose of demonstrating TDD so we won't be rendering anything to the DOM.

```
As a ship captain,
So I can get on my ship,
I want my ship to have a starting port.
```

```
As a ship captain,
So I can get holidaymakers on their way to their destination,
I want my ship to set sail from the port.
```

```
As a ship captain,
So I can get holidaymakers to their destination
I want my ship to dock at a port.
```

```
As a ship captain,
To ensure the safety of my passengers,
I don’t want my ship to set sail if the weather is stormy.
```

```
As a ship captain,
So I can dock my ship,
I don’t want my ship to dock at a port if the port is full.
```

## Our objects and methods

| Object  | Methods        |
|---------|----------------|
| Ship    | getStartingPort setSail dock |
| Port    | isFull         |
| Weather | isStormy       |

[Continue to Part 1](lesson1_page1.md)
