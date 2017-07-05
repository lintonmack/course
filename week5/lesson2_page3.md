:twisted_rightwards_arrows: Switch Driver/Navigator roles, if you haven't already done so.

## Encapsulating the DOM update

The below code is currently presenting our stations/current station on the DOM:

```js
$.each(altrinchamToAshtonUnderLyne.getStations(), function (stationIndex, station) {
  var css = ''
  if (tram.getCurrentStation() === station) {
    css += '-current'
  }

  var stationHTML = '<div class="station">'
  stationHTML += '<div class="circle ' + css + '"></div>'
  stationHTML += '<div class="name">' + station.getName() + '</div>'
  stationHTML += '</div>'

  $('#stations').append(stationHTML)
})
```

The issue is that every time the state of our application changes (a.k.a the tram moves to a different station) then we're going to need to perform this DOM update again. It would be better if we encapsulated this code inside of a function, and then called the function initially, and then on every state change.

1) Wrap the above code inside a function called `updateDOM`:

```js
function updateDOM() {
  $.each(altrinchamToAshtonUnderLyne.getStations(), function (stationIndex, station) {
    var css = ''
    if (tram.getCurrentStation() === station) {
      css += '-current'
    }

    var stationHTML = '<div class="station">'
    stationHTML += '<div class="circle ' + css + '"></div>'
    stationHTML += '<div class="name">' + station.getName() + '</div>'
    stationHTML += '</div>'

    $('#stations').append(stationHTML)
  })
}
```

2) Every time we call the method, we want to make sure we clear the innerHTML of our `#stations` element before we append any content otherwise we'll just keep appending to it. We can do this with `$('#stations').html('')`. Add right at the beginning of your function block:

```js
function updateDOM() {
  $('#stations').html('')

  $.each(altrinchamToAshtonUnderLyne.getStations(), function (stationIndex, station) {
    var css = ''
    if (tram.getCurrentStation() === station) {
      css += '-current'
    }

    var stationHTML = '<div class="station">'
    stationHTML += '<div class="circle ' + css + '"></div>'
    stationHTML += '<div class="name">' + station.getName() + '</div>'
    stationHTML += '</div>'

    $('#stations').append(stationHTML)
  })
}
```

3) Now the DOM update is encapsulated into its own function, you will need to call the function. Add a call underneath:

```js
updateDOM()
```

## Wiring up the Next Station button

We want to add an *event handler* that determines what happens when our **Next Station** button is clicked. To do this with jQuery, we use `$(<css_selector>).click(<callback_function>)`, where **<callback_function> is a function we pass which handles what happens after the click event.

1) Create a `.click` event handler for the selector `#nextStationBtn` and pass an empty anonymous function as the second argument:

```js
$('#nextStationBtn').click(function () {

})
```

2) Inside the function, we want to call `tram.drive()` and then afterwards we should call `updateDOM()` to reflect the fact our tram has a new current station:

```js
$('#nextStationBtn').click(function () {
  tram.drive()
  updateDOM(altrinchamToAshtonUnderLyne, tram)
})
```

## Wiring up the Reset button

1) Our Tram prototype doesn't currently have a method to reset the Tram's route. Inside `js/tram.js`, at the end of the prototype, add a new method called `reset` and inside the function block, add code that sets the Tram's `_currentStation` to `_route.getStations()[0]` (a.k.a send it back where it started):

```js
reset: function () {
  this._currentStation = this._route.getStations()[0]
}
``` 

2) Now add another click event handler for `#reset`, but this time call `tram.reset()` before calling `updateDOM()`:

```js
$('#reset').click(function () {
  tram.reset()
  updateDOM(altrinchamToAshtonUnderLyne, tram)
})
```