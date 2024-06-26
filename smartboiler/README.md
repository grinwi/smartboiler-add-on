# Home Assistant Add-on: Smart Boiler

# SMART BOILER
This is a README for the Smart Boiler application, used to decrease energy usage for heating water in a boiler. This is achieved by learning household consumption trends and heating water above the emergency temperature just before predicted consumption.

Link to the GitHub repository: <https://github.com/grinwi/smartboiler>.

## What's it all about?
This project was undertaken as a master's thesis at FIT VUT Brno. 
The goal was to find a solution for cutting costs by predicting household inhabitants' behavior with machine learning. Machine learning was utilized to train an LSTM network on historical data from a smart home. 
Based on the prediction of heat consumption from the water boiler, the algorithm included in controller.py achieves a reduction in the average temperature of the water in the boiler, lowering energy losses, and the energy needed to deliver heat into the boiler.
This solution assumes that the user has a boiler whose heating can be controlled by a Shelly smart plug <https://www.shelly.com/en/products/shop/shelly-plus-1-pm>.
Another requirement is a Home Assistant running in the required household with an InfluxDB database, which stores household data as well as weather information, the presence of devices via NMAP <https://www.home-assistant.io/integrations/nmap_tracker/> integration, and a flow meter with a temperature sensor placed on the output of the boiler. Another temperature sensor must be placed inside the boiler casing to control the heating based on the water temperature in the boiler.
Users can also utilize their Google Calendar to turn off the heating, for example, when they are on holiday. Another function using the calendar is heating to a needed temperature when unusually high consumption is expected.

The Home Assistant Add-On repository can be found at this address: <https://github.com/grinwi/smartboiler-add-on>.
![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]


[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg

