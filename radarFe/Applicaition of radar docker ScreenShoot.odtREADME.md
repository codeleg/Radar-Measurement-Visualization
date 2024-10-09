Radar Measurement Visualization
This project is a web-based application designed to visualize radar measurements in polar coordinates. The application connects to an emulated radar measurement component running as a Docker container, reads the detected targets through WebSocket, and displays them on a polar graph. The user can also adjust radar parameters via an API.

Features
Real-time Radar Data Visualization: The application connects to a WebSocket server to receive radar data, processes it, and visualizes detected targets in polar coordinates.
Parameter Configuration: Users can adjust radar measurement parameters (such as rotation speed, measurements per rotation, and target speed) through an API using an intuitive user interface.
Prerequisites
To run the project, you need the following software installed on your system:

Docker: To run the radar emulator container.
Node.js (Optional): To install and use wscat for testing WebSocket connections.
Setup Instructions
Step 1: Run the Radar Emulator
Download the radar emulation service Docker image:

bash
Copy code
docker pull iperekrestov/university:radar-emulation-service
Run the radar emulation service:

bash:
docker run --name radar-emulator -p 4000:4000 iperekrestov/university:radar-emulation-service
This command will start the radar emulator on port 4000.

Step 2: WebSocket Connection
To test the WebSocket connection, you can use wscat:

Install wscat globally:

bash: 
npm install -g wscat
Connect to the WebSocket server:

bash:
wscat -c ws://localhost:4000
You will start receiving radar measurement data in real-time.

Step 3: Run the Application
Clone the repository:

bash :
git clone https://github.com/yourusername/radar-visualization.git
Open the project directory and launch the web application using your preferred method (e.g., by opening index.html in a browser).

WebSocket Message Format
The WebSocket server sends radar data in the following format:

json:
{
  "scanAngle": 90,
  "pulseDuration": 1,
  "echoResponses": [
    {
      "time": 0.000012,
      "power": 0.05
    },
    {
      "time": 0.000024,
      "power": 0.02
    }
  ]
}
scanAngle: The angle at which the radar scan is taking place (in degrees, ranging from 0 to 360).
pulseDuration: The pulse duration of the radar signal in microseconds.
echoResponses: An array of detected objects, each containing:
time: The time it took for the radar signal to reach the object and return (in seconds).
power: The strength of the reflected signal (between 0 and 1).

Step 4: Adjust Radar Parameters
You can adjust the radar's behavior through the provided API. For example, you can change the number of measurements per rotation, rotation speed, or the target speed. Use the following curl command to update the parameters:

bash:
curl -X PUT http://localhost:4000/config -H "Content-Type: application/json" -d '{
    "measurementsPerRotation": 360,
    "rotationSpeed": 10,
    "targetSpeed": 500
}'
API Parameters
measurementsPerRotation: The number of measurements the radar takes during one full rotation. Default: 360.
rotationSpeed: The speed at which the radar rotates (measured in rotations per minute, RPM). Default: 60.
targetSpeed: The speed of the targets being detected by the radar (measured in kilometers per hour, km/h). Default: 100.
beamWidth: The width of the radar beam (in degrees). Default: 1.
numberOfTargets: The number of targets to simulate. Default: 1.
emulationZoneSize: The size of the area in which the radar is emulating (in kilometers). Default: 200.
Visualizing Data
The received radar data is processed and displayed on a polar graph using libraries like Plotly. The detected targets are plotted based on their angle (azimuth) and distance (calculated from the time it takes for the radar signal to return).
