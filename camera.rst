Camera
======

cameraOn(double imagePeriod, [int maxHeight, int maxWidth, Function callback]) : void
  Continuously capture camera frames. If a callback is specified it is given the data base64 encoded.

.. code-block:: html

    <html style="width:100%; height:100%; overflow:hidden">
    <body style="width:100%; height:100%; overflow:hidden; margin:0">
    <img width="640" height="360" id="image" />
    <script>
    function main() {
	if (WS.scriptVersion(1)) return;
	WS.cameraOn(.5, 180, 320, function(data) {
	    document.getElementById('image').setAttribute('src', 'data:image/jpg;base64,' + data);
	});
    }
    window.onload = main;
    </script></body></html>

cameraOff() : void
  Turns off camera

.. code-block:: html

    <html style="width:100%; height:100%; overflow:hidden">
    <body style="width:100%; height:100%; overflow:hidden; margin:0">
    <img width="640" height="360" id="image" />
    <script>
    function main() {
	if (WS.scriptVersion(1)) return;
	WS.cameraOn(.5, 180, 320, function(data) {
	    document.getElementById('image').setAttribute('src', 'data:image/jpg;base64,' + data);
	});
	setTimeout(function () {
	    WS.cameraOff();
	}, 5000);
    }
    window.onload = main;
    </script></body></html>


cameraPhoto([Function callback]) : void
  Take a picture and save it to the SD card and callback to `callback(String path)`. Can be used as src attribute for an image.


.. code-block:: html

    <html style="width:100%; height:100%; overflow:hidden">
    <body style="width:100%; height:100%; overflow:hidden; margin:0">
    <img width="640" height="360" id="image" />
    <script>
    function main() {
	if (WS.scriptVersion(1)) return;
	WS.cameraPhoto(function(location) {
	    document.getElementById('image').setAttribute('src', 'file://' + location);
	});
    }
    window.onload = main;
    </script></body></html>


cameraPhotoData([Function callback]) : void
  Take a picture and callback to `callback(String imageb64)` with a base64 encoded jpeg.

.. code-block:: html

    <html style="width:100%; height:100%; overflow:hidden">
    <body style="width:100%; height:100%; overflow:hidden; margin:0">
    <img width="640" height="360" id="image" />
    <script>
    function main() {
	if (WS.scriptVersion(1)) return;
	WS.cameraPhotoData(function(data) {
	    document.getElementById('image').setAttribute('src', 'data:image/jpg;base64,' + data);
	});
    }
    window.onload = main;
    </script></body></html>

cameraVideo([Function callback]) : void
  Record a video and save to the SD card.

.. code-block:: html

    <html style="width:100%; height:100%; overflow:hidden">
    <body style="width:100%; height:100%; overflow:hidden; margin:0">
    <script>
    function main() {
        if (WS.scriptVersion(1)) return;
        WS.cameraVideo(function (location) {
            WS.log(location);
        });
    }
    window.onload = main;
    </script></body></html>
