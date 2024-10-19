### Hi there 👋
### Fala pessoal 👋

### SEJAM TODOS BEM-VINDOS
### WELCOME TO ALL OF YOU

- 🔭 I’m currently working on Cyber Systems, C, C++ and Embedded Linux (kernel, U-boot and DT mostly), MSc in Electrical Eng...
  
- 🌱 I’m currently learning AI, Federated Learning in Edge Computing and Cybersecurity...
  
- 📫 How to reach me: Linkedin: elieldermelo

- 👯 I’m looking to collaborate on Embedded Software... hard challenges that demands hard work

- ⚡ Interests: Brazilian soccer (São Paulo), Rock n'roll, theology, philosophy, ...


<!--
**elielderbm/elielderbm** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

# IoT Challenge

`camera_container` directory contains an application with a couple of routes simulating an API used to access stored video metadata from a specific model of security camera.

Your task is to create an application that consumes this API and aggregates the data it provides. The camera API is quite verbose and slow, so it's beneficial to group the data for faster future access while consuming less bandwidth.

The new API should be able to respond about the camera's stored videos, filtering for start time, end time and video type.

The expected outcome of this challenge is a well-documented, tested, and efficient application (including both the new API and the `camera_container` app). Additionally, it is recommended to create a Docker Compose configuration that integrates both applications.

### Additional Data:
```
record_type:
    NormalRecord: 0x1
    AlarmRecord: 0x2
    MotionRecord: 0x4
```

## API Description - App Specification

This new API works to manage data better and make it easy to access. It has an application that creates a database to store information, which helps make data available faster and uses less bandwidth. The database is updated every day to include data from the day before. Another part of the API has similar routes to the old one but adds three more to filter and collect data based on start time, end time, and video type. This part gets data from the database and shares it through the API. There is also a section that uses metadata to simulate the camera API, which helps in testing. Finally, the API can be deployed in a Docker environment using specific commands to run everything together.

This new API works as following:

- `aggregator` directory contains an application to create an Database and store data to make its data available faster and consuming less bandwidth as asked. The Database is updated once a day in specific time, 00:00:10, pointing to the previous day.

- `camera_container` directory contains an application with the same routes as the previous implementations but with three more routes added to filter and collect data by start time, end time and record video type. It collects data from Database and make it available through API.

- `mock` directory refers to the metadata used to simulate the camera API.

- `docker-compose.yml` deploy this new API, with an aggregator and a camera_container app in Docker Environment and its deployment can be done by working as commands below:

### New API - App Deployment

#### First of all make sure that Docker and Docker Compose is installed in your environment (It was built, tested and deployed in Linux-Ubuntu 22.04)

`git clone https://github.com/elielderbm/iot-challenge.git`

`cd iot-challenge`

`docker-compose up --build &`

By sending this commands the application is deployed.

### Testing the API

`http://localhost:5000/month/8`

`http://localhost:5000/month/8/day/31`

`http://localhost:5000/record_type/1`

`http://localhost:5000/start_time/00:00:00`

`http://localhost:5000/end_time/23:59:59`






