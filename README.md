Microservices To-Do Application

This simple application follows the Microservice architecture, which enables independent development, deployment, and scaling of individual services. Each service is designed to perform a specific function and can be built using any technology stack. The following key aspects define this application:

------Services Overview------
Task Service (task-service):
Manages tasks and their assignment to users.

* Port: 5002 (available port on your machine)
* Functionality:
    Create tasks.
    Assign tasks to specific users by interacting with the User Service.
    Fetch tasks for a particular user.
    Delete tasks

User Service (user-service):
Handles user-related functionality.

*Port: 5001 (available port on your machine)
*Functionality:
    Register and Login user.
    Provide user-related data to other services, like the Task Service.
    
Frontend Service (todo-frontend):
Provides the user interface for interacting with the application.

*Port: 3000 (available port on your machine)
*Functionality:
    Display tasks and users.
    Allow users to create and manage tasks.

------How to Run the Application-------
This project uses Docker Compose to manage and run the services. Below are the steps to set up and run the application: 

Prerequisites:-
* Docker and Docker Compose installed on your machine.
* An external Docker network (todo-app-network) created. (because for this i use my existing network.you can create your own network for this using docker compose )Use the following command to create it if it doesn’t exist:
   docker network create todo-app-network. (All services communicate over the todo-app-network Docker network.)

-----Steps to Run------

1.Clone the repository and ensure all three services are in their respective directories:   

Microservice_DevOps/ (any folder name)
├── task-service/
├── user-service/
├── todo-frontend/
└── docker-compose.yml

links for each services

  Task Service - https://github.com/Kavindu97007/Todo-task-service-backend
  User Service - https://github.com/Kavindu97007/Todo-user-service-backend
  Frontend     - https://github.com/Kavindu97007/Todo-frontend

Note:-

* Change ports based on your machine's availability.
* Since existing docker images are used; need to have a docker images with exact names for each services in docker-compose.yml or you can create images using build context in docker-compose.yml.
Eg: build:
      context: ./task-service # Path to the directory containing the Dockerfile for task-service
      dockerfile: Dockerfile  # Optional, specify the Dockerfile name if it's not the default 'Dockerfile'
  like this way you can create images for other services as well.

2. Use Docker Compose to build and run the services:

   docker-compose up --build

3. Access the application:

   http://localhost:3000 (using your port number)


------Technologies Used-------

Backend: Node.js/Express
Frontend: Reactjs
Database: MongoDB
Containerization: Docker

   Special Notes:-

   Since this application follows the Microservice architecture, each service is independent and can be built using any technology stack that suits its specific requirements.

  * Frontend and Backend Communication:
  
      The frontend service communicates with backend services (task-service and user-service) over HTTP requests.
      Since the frontend and backend services operate on different domains, CORS (Cross-Origin Resource Sharing) has been implemented to handle secure cross-domain communication.
  
  * Inter-Service Communication:
  
      The task-service communicates with the user-service using HTTP requests using RESTful endpoints.
      
  * Separate Databases for Each Service:
  
      The task-service and user-service each have their own dedicated database, ensuring data isolation and scalability.
      This approach helps in better separation of concerns and allows each service to manage its data independently.
    
  * Customizable Configuration:
  
      The application’s services are containerized using Docker and can be managed through the docker-compose.yml file.
      Users can customize service ports and database configurations based on their requirements.
    
  * Flexible Technology Stack:
  
      While this application uses specific tools and frameworks, the Microservice architecture allows developers to replace or modify the technology stack of any service, as long as the communication protocols (e.g., HTTP) are maintained.   

    
