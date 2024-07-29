# gps-tracker

<!DOCTYPE html>
<html>
<head>
  <title>GPS Tracking Map</title>
  <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_GOOGLE_MAPS_API_KEY"></script>
  <script>
    function initMap() {
      var urlParams = new URLSearchParams(window.location.search);
      var data = JSON.parse(urlParams.get('data'));
      
      var map = new google.maps.Map(document.getElementById('map'), {
        zoom: 10,
        center: {lat: 0, lng: 0}
      });

      data.forEach(function(device) {
        var latLng = new google.maps.LatLng(device.Latitude, device.Longitude);
        new google.maps.Marker({
          position: latLng,
          map: map,
          title: device.DeviceID
        });
      });
    }

    window.onload = initMap;
  </script>
</head>
<body>
  <div id="map" style="height: 100%; width: 100%;"></div>
</body>
</html>
