Cars in the Parking Lot - with hints
------
Below is an object called parkingLot. It has two methods that need populating: `parkCar`, which should take a `carName` and add it to the object's `cars` array; and `getNumberOfCars`, which should `return` the number of cars parked (a.k.a the length of the object's `cars` array).

```js
var parkingLot = {
  cars: [],
  parkCar: function (carName) {

  },
  getNumberOfCars: function () {

  }
}

parkingLot.parkCar('peugeot')
parkingLot.parkCar('citroen')
console.log(parkingLot.getNumberOfCars()) // 2
console.log(parkingLot.cars) // ['peugeot', 'citroen']
```

Hints
------
* `parkCar` should call the `.push` method on the `cars` array. You can access methods and properties from within an object with the `this` keyword. 
* `getNumberOfCars` should call the `.length` property on the `cars` array. Again, you should use the `this` keyword to help you find that array.