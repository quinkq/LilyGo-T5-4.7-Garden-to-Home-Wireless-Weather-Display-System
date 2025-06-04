My take on <b>LilyGo-EPD-4-7-OWM-Weather-Display</b> with a few adaptations for own purposes. Same as original, developed using PlatformiO.

<br/>
<br/>

<img src="https://github.com/user-attachments/assets/83122ad7-aca4-48b6-8d79-b33b7255faec" width="533" height="400">

<br/>
<br/>

Maintains original functionality - downloading OWM Weather via API, configuration AP, E-INK display handling and now:
- employed FreeRTOS to facilitate concurrent sensor readings, calculations, running webserver and future tasks
- introduced i2c sht40 sensor for indoor temperature and humidity readouts
- added ESP-NOW wireless data exchanges with auxiliary esp32 that reads bme280/sht40 environment sensors and sends them to the master (esp32s3 handling e-ink display) in between deep sleep periods
- storing/buffering data as .csv on sd card
- async webserver for an easy access to recent and saved historical data using graphs, converting .csv to jsons
- configuration webserver uses same async server now and offers OTA update functionality
- employed external tactile switch for display selection/switching to better handle available data (more to be added)
- included modified original font converting script to create headers with polish diacritics
<br/>
  
<img src="https://github.com/user-attachments/assets/f52dc17b-2dce-4d8e-971e-f06844adc592" width="533" height="708">
<img src="https://github.com/user-attachments/assets/80480141-9f3e-458a-a08e-a9a692c5db92" width="533" height="400">
<img src="https://github.com/user-attachments/assets/d98e1fc9-a67f-4e72-9a7a-6392e64241f0" width="533" height="400">  

<br/>
<br/>


**Auxiliary station:**

This is a remote part of my weather station, meant for measuring temperature/humidity/pressure and sending it via ESP-NOW to the main unit - ESP32S3/Lilygo T5 4.7 E-paper display. 
Station consists of 2 main elements:

Main case, housing:
- ESP32C3 microcontroller
- MCP73871 solar charge controller
- TPS63020 buck-boost converter (3.3 V output)
- solar panel holder for 1 W 6 V solar panel (110x60x2.5 mm)
- 18650 Li-ion cell 3.7 V
- USB-C port for backup battery charging

Electronics holding part is meant to be inserted from below into the shell to avoid water ingress. Assembly requires 6 x M4 hex nuts and DIN 7991 bolts (or similar, at least 15mm long). It's also meant to hold 2 mesh filters on both sides to prevent insect infestation.
Shell features heat shielding double roof and has 2 slanted ventilation ports on both sides. It holds 4 x M5 hex nuts on the bottom to allow bolting down station in place.
     
Stevenson screen temperature tower
- houses 2 temperature/humidity/pressure sensors - SHT40 and BME280
- assembly requires 6 x M3 hex nuts
- 3 x DIN 976 M3 vertical rods

<img src="https://github.com/user-attachments/assets/ff265706-a485-4416-9e9e-c670f0703ca8" width="533" height="400">
<img src="https://github.com/user-attachments/assets/95319df9-c829-40e5-94ff-6c9d3cd74f79" width="533" height="400">
<img src="https://github.com/user-attachments/assets/14c694b6-0cba-430c-b175-a58802c0a82c" width="533" height="708">
<img src="https://github.com/user-attachments/assets/98b82852-1dbc-4b7d-8d0f-bd9042ccf343" width="533" height="400">
<img src="https://github.com/user-attachments/assets/e19d3365-910b-4681-8378-3d9202ba643d" width="533" height="400">

My 3D Models:
- Display case [Lilygo T5 4.7" V2.3 E-Paper display case](https://www.printables.com/model/1277128-lilygo-t5-47-v23-e-paper-display-case)
- Data gathering station [Remote weather data gathering station](https://www.printables.com/model/1277283-steven-remote-weather-data-gathering-station)

PLANNED:
- adding rainfall measurement and wind force/direction to the auxiliary ESP32 measuring station








