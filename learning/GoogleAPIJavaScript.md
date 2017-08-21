<div id="map"></div>

<script src="https://maps.googleapis.com/maps/api/js?key=AIzaSyCvgwyN7k5XzbFVYKLUQHWOdFpsda2uUFk&callback=initMap" async
    defer></script>

# Google Maps API With JavaScript

### Overview
Team Narwhal followd the directions from the [Dart Google Maps Documentation](https://github.com/a14n/dart-google-maps) along with referencing the [Official Google Maps API for JavaScript](https://developers.google.com/maps/documentation/javascript/)

The Google Maps API with JavaScript will allow us to place a Google Map embeded directly into our app. With the Dart implementation, we are able to do this simply. Our goal is to provide a visual dot to dot destination to the user for the restaurant they are viewing. Our goal is to retrieve the latitude and longitude for the user using the current browser and, using the Hamster API, retrieve the latitude and longitude for the restaurant, and display this on Google Maps. We also want to provide a link to open the direction directly in Google Maps.

### Creating The Map
To create the map, we firstly want to get a link to the maps script. The script requires an API key to be injected including the callback routine. Using the documentation provided by the [Dart Google Maps Package](https://github.com/a14n/dart-google-maps), we added the script to the HTML page, added the package to our library, and added some additional code to our component. 

```html

    <script src="https://maps.googleapis.com/maps/api/js?key=MAPS-API"></script>
```

We followed the example provided by the project under [Services/Directions-Simple](https://github.com/a14n/dart-google-maps/tree/master/example/08-services/directions-simple)

The following script creates the map and has hard coded latitude and longitude. 

For the example, we wanted to get directions from The Forge in Des Moines to a local restaurant, Big City Burger. The following outputs the componet DIV and populates the DIV with the map. 

```dart
part of over_react.web.features.shared;

DirectionsRenderer directionsDisplay;
final directionsService = new DirectionsService();
GMap map;

@Factory()
UiFactory<MapsProps> Maps;

@Props()
class MapsProps extends UiProps {
  LatLng origin;
  LatLng destination;
}

@State()
class MapsState extends UiState {
}

@Component()
class MapsComponent<T extends MapsProps, S extends MapsState>
    extends UiStatefulComponent<T, S> {

  @override
  setInitialProps() {
    newProps()
    ..origin= new LatLng(41.584272, -93.6356068)
    ..destination= new LatLng(41.584272, -93.6356068);
  }

  @override
  componentDidMount() {

    directionsDisplay = new DirectionsRenderer();
    final mapOptions = new MapOptions()
      ..zoom = 7
      ..center = props.origin
      ..zoomControl=false
      ..scaleControl=true;
    map = new GMap(document.getElementById('map-canvas'), mapOptions);
    directionsDisplay.map = map;
    final request = new DirectionsRequest()
      ..origin = props.origin
      ..destination = props.destination
      ..travelMode = TravelMode.WALKING;
    directionsService.route(request, (response, status) {
      if (status == DirectionsStatus.OK) {
        directionsDisplay.directions = response;
      }
    });
  }

  render() {
    return ((Dom.div()..id="map-canvas")());
  }
}
```

Additional CSS was added to add height of 300px to the `map-canvas` for demo purposes.