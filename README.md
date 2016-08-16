# Google-Nest-Prototype

The temperature and humidity sensors send their reading values to Arduino.
From the Arduino the data is sent in particular format through the transmitter to the Raspberry Pi.
The Raspberry Pi has a receiver that receives the data format values and publishes data to the MQTT topics.
MQTT sends the data to Kafka on specified topics through Mqtt-Kafka Bridge written in Python to connect it to the Kafka instance.
The messages received at Kafka are passed to the Apache Spark for stream analytics. We created predictive models for temperature and humidity with the help of training dataset.
With the help of this model, we will predict the temperature and humidity for next 24 hours.
The prediction results are stored in ElasticSearch.
The data stored in ElasticSearch is sent over to Kibana where we are able to  visualize the predicted data. We built a dashboard in Kibana with all the graphs and embedded it in our web application.
We developed a NodeJS server which will communicate with web client and can control the thermostat from web UI.
NodeJS server sends sensor state, current temperature and humidity values. We can control HVAC heating coefficient from web application. 
We used openweather API to display real-time outside temperature according to geolocation and changing the background of application dynamically.
On web application load, the array for current time and next 24 hours values are sent over Kafka to predict dependent temperature and humidity in Apache Spark.
