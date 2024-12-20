Key Components:

WebSocket Connection:
Establishes a connection to a radar emulation service at ws://localhost:4000.
Handles incoming messages containing radar scan data.

Data Processing:
Parses incoming data messages that include:
scanAngle: The angle at which the radar scanned.
echoResponses: An array of echo responses containing time and power.

Calculates distance using the formula:
Distance= (SPEED_OF_LIGHT×time ) / 2
 
Updates arrays for angles, distances, and signal strengths for visualization.

Visualization:
Uses Plotly.js to render a polar scatter plot based on the updated data.
Configures the plot with radial and angular axes and color scales representing signal strength.

Radar Parameter Updates:
Provides a function to update radar parameters (e.g., measurements per rotation, rotation speed, and target speed) through a REST API.
Sends configuration updates to http://localhost:4000/config using a PUT request.

Error Handling:
Implements logging for various WebSocket events, including opening, closing, and errors, along with data format validation.
