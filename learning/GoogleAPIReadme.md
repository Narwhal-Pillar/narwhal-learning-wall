# Google Maps API Wrapper for Go Learning

To learn more about the library we used to easily communicate with the Google Maps API, we utilized the [Google Maps Services Client Library].

The [Google Maps Services Client Library] provides a quick and easy way to connect to not only the Google Maps API, but also to retrieve information from the Google Places API. Only one key is necessary to access all of the Google APIs associated with this plugin, the Google Maps API key. 

As part of learning, we utilized the free version of the Google Maps API, so the number of requests we could send out to the API were limited to 10 a second. Per the [Google Maps Services Client Library], this is perfect for the free version.

#### Returning the Maps response in a JSON format:
```go
json.NewEncoder(writer).Encode(resp)
```

### Gotchas
... Coming soon ;-)

### References
Please refer to our [Working Prototype] Prototype utilizing the Google Maps API in Go. 

[Google Maps Services Client Library]: https://github.com/googlemaps/google-maps-services-go
[Working Prototype]: https://github.com/Narwhal-Pillar/hamsterApi/blob/google-api/app/features/places/place_controller.go