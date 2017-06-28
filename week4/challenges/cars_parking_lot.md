Cars in the Parking Lot
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

***
:bulb:

Want to challenge yourself further? Add a `removeCar` method that accepts a `carName` as a parameter and removes that `carName` from the object's array.
***

Stuck? [See hints](https://github.com/MCRcodes/course/blob/master/week4/challenges/cars_parking_lot_hints.md).