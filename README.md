1-Application of Radar Docker Screenshot (ODT file):
I wanted to show its dimensions with screenshots in this file.
This document explains how to track the coordinates of target points sent to a radar application running in a backend Docker container.
It provides instructions on how to establish a connection to this Docker container.

2-Application of Radar Docker ScreenshotREADME (README.md):
It explains in writing how to connect to a docker container and how to send data.

3-index.html:
This HTML file is designed to visualize the data received from the Docker container using a polar chart.
It allows us to monitor the incoming points every second, providing real-time visualization of the radar data.
You can understand the script better by following the comment lines.

4-polarGrafPointMeasurement.png:
This image file is a screenshot of the designed HTML page, illustrating how the polar chart appears with the tracked points visualized.

5-README.md 
Showing point on polar chart explanation
This application establishes a WebSocket connection with a radar emulation service to process and visualize radar scanning data in real-time. It parses incoming messages to extract the scanning angle and echo responses, performing distance calculations accordingly. The updated data is visualized using a polar scatter plot with Plotly.js. Additionally, there is a function to send configuration updates for radar parameters through a REST API. The application also manages WebSocket events (connection opening, closing, errors) and data format validation.


