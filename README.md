# 🎹 NicePiano

NicePiano is an **online web application** which enables users to **play a virtual piano** together with other users, **in real time**.
The application can be used via a connected keyboard (or digital piano) which supports the **Musical Instrument Digital Interface (MIDI) protocol**, which sends messages to the browser according to the standard specification.

<div align="center">

![room](https://user-images.githubusercontent.com/23276420/219973443-ef946388-7afb-48c3-9d98-e8ba6f48f9bd.jpeg)

</div>

In the repository, the code for the frontend and backend is available as a separate submodule respectively in [`nice-piano-frontend`](https://github.com/dotmat3/nice-piano-frontend) and [`nice-piano-server`](https://github.com/dotmat3/nice-piano-server).

In the file [`Report.pdf`](https://github.com/SkyLionx/nice-piano/blob/main/Report.pdf), an in-depth review of the work and challenges encountered during the deployment of this project is presented along with a verification phase to test the limits of the scalability of the system. Moreover, a presentation is also available in the file [`Presentation.pdf`](https://github.com/SkyLionx/nice-piano/blob/main/Presentation.pdf) which summarizes the work which has been done and the results obtained from the stress test of the system.

## Features
- 🔒 Creation of **virtual rooms** to host private sessions
- 🎹 **Physical piano support** using the MIDI protocol
- 🔴 **Record a performance** that can be played back at a later time
- 🔄️ **Loop** a pre-recorded performance
- 🎵 **Waterfall visualization** of past played notes
- 📶 **Latency indicator**

## System Architecture

<div align="center">

![nice-piano-arch](https://user-images.githubusercontent.com/23276420/219973274-fd501991-a7a3-4e5a-ba10-1f07fc5d4cb3.png)

</div>

The majority of the system has been deployed on the **AWS cloud computing platform** using the following services:
- Amazon Cognito for authentication
- DynamoDB to store users piano performances
- CodePipeline and CodeBuild (and S3) for CI/CD
- ElasticBeanstalk in order to deploy the web app using the Docker engine
  - 1-3 EC2 t2.micro instances with automatic scaling policy
  - Load balancer

## Contributors

<a href="https://github.com/SkyLionx" target="_blank">
  <img src="https://img.shields.io/badge/Profile-Fabrizio%20Rossi-green?style=for-the-badge&logo=github&labelColor=blue&color=white">
</a>
<br /><br />
<a href="https://github.com/dotmat3" target="_blank">
  <img src="https://img.shields.io/badge/Profile-Matteo%20Orsini-green?style=for-the-badge&logo=github&labelColor=blue&color=white">
</a>

## Technologies

The whole system is based on the use of **WebSockets** in order to provide bidrectional real-time connection between the clients and the server.
In order to build the **front-end**, the following JavaScript libraries were used:
- React.js framework
- Tone.js and @tonejs/Piano to produce piano sounds
- aws-amplify for Amazon Cognito to handle user authentication
- Browser MIDI API (Chrome, Edge, Opera) to handle the PC-Piano communication

For the **back-end**, instead the following technologies were used:
- Docker engine with Dockerfile
- Node.js runtime
- aws-sdk for communication with DynamoDB to store user piano performances
- Socket.IO to handle the rooms mechanism
- Redis for message exchanges among different server instances
