Services Overview
Postgres

Image: We're using PostgreSQL version 13.
Environment Variables: Configured to set up our database name, user, and password.
Volumes: Ensures our database data persists even if the container restarts.
Ports: Exposes port 5432 for external database interactions.
Backend

Build: Specifies where to find our backend code for building the Docker image.
Volumes: Allows live changes during development by connecting the backend directory to the container.
Ports: Exposes port 8000 for accessing our backend API.
Depends On: Ensures PostgreSQL is up before starting the backend.
Environment Variables: Sets up our database connection and CORS settings.
Frontend

Build: Specifies the frontend directory for building the Docker image.
Command: Runs our frontend using npm run dev for development.
Volumes: Mounts the frontend directory for container use.
Ports: Exposes port 5173 for accessing the frontend app.
NGINX

Image: Uses the latest NGINX image.
Volumes: Mounts our custom NGINX configuration.
Depends On: Starts only after frontend and backend are running.
Adminer

Image: Uses the latest Adminer image for managing databases.
Restart Policy: Always restarts for high availability.
Ports: Exposes port 8080 for Adminer access.
Environment Variables: Sets the default database server.
NGINX Proxy Manager

Image: Uses the latest NGINX Proxy Manager image.
Restart Policy: Restarts unless manually stopped.
Ports: Exposes ports 81, 80, and 443 for dashboard access and handling traffic.
Volumes: Mounts directories for proxy settings and SSL certificates.
Depends On: Starts after NGINX and Adminer.
Why We Use NGINX and NGINX Proxy Manager
NGINX

Reverse Proxy: Routes requests based on URL patterns, enhancing security and load balancing.
Static File Serving: Efficiently serves static files, boosting backend performance.
SSL Termination: Manages HTTPS requests and forwards them as HTTP to the backend.
NGINX Proxy Manager

User-Friendly Interface: Web-based interface simplifies configuration, domain management, and SSL certificate handling.
SSL Management: Automates SSL certificate setup and renewal for secure connections.
Access Control: Allows easy setup of access rules and redirections, adding security layers.
How to Run the Project
Clone the Repository:

bash
Copy code
git clone https://github.com/teetoflame/devops-stage-2.git
cd your-repo
Build and Run Docker Containers:

bash
Copy code
docker-compose up --build
Access the Applications:

Frontend: http://localhost:5173
Backend: http://localhost:8000
Adminer: http://localhost:8080
NGINX Proxy Manager: http://localhost:81
Configure Domains and SSL in NGINX Proxy Manager:

Open http://localhost:81 in your browser.
Log in with default credentials (admin@example.com / changeme).
Add your domains and configure SSL settings as needed.
Conclusion
This Docker setup demonstrates a solid foundation for a full-stack web app using NGINX and NGINX Proxy Manager. It's designed to scale easily, enhance security, and simplify management whether you're in development or production environments
