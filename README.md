# Docker Multi-Service Application

## Project Overview
This lab focuses on learning how to use Docker and Docker Compose to deploy a multi-service application. The system is an IT ticket dashboard made up of three services: Apache2, Flask, and MariaDB. Apache acts as a reverse proxy and is the only service exposed to the outside world. Flask handles the application logic and API requests, while MariaDB stores the ticket data. The goal of this lab is to understand how these services work together in containers and how Docker Compose manages their communication and startup order.

## Prerequisites
To complete this lab, you need a working Ubuntu Server virtual machine with Docker and Docker Compose installed. You also need VS Code with the Remote – SSH extension set up so you can connect to your VM. Git must be installed so you can clone the repository. Finally, your user should be added to the Docker group so you can run Docker commands without needing sudo every time.

## Getting Started
First, clone the repository onto your VM and navigate into the project directory. Then create your environment file by copying the provided example file into a new .env file. You will need to fill in the database credentials in this file so all services can connect properly. Next, stop the Apache service running on the VM to free up port 80. After that, build and start the application using Docker Compose with the build flag. Once everything is running, you can check the status of your containers using docker compose ps.

## Configuration
This project uses environment variables stored in a .env file to configure the database and application settings. The MariaDB service uses variables for the root password, database name, username, and password. The Flask application uses similar variables to connect to the database, including the database host, which is set to the service name “db” so Docker’s internal DNS can resolve it. All services are connected through a shared Docker network, allowing them to communicate using service names instead of IP addresses.

## Verification
To verify the application is working correctly, first run docker compose ps and confirm that the database and app containers are marked as healthy. Next, test the API by running curl requests against the health endpoint and the tickets endpoint to confirm the backend is working. Then open the application in a browser using the VM’s IP address on port 80 and confirm that the ticket dashboard loads and shows a green “API healthy” indicator. You should also verify that you can create new tickets and that they persist even after restarting the database container. Finally, run the provided check script and ensure all tests pass.

## Feedback (Optional)
N/A

N/A
