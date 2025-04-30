# SocketForum - Forum Website with Scheduled Posts
This repository contains a basic forum application with user authentication, public post creation, and post scheduling capabilities. The application leverages web sockets for real-time updates, enhancing user interaction.

# Technologies Used (Backend)
* Python: Flask serves as the web framework to manage HTTP requests and responses.
* MongoDB: Stores user data, posts, and scheduled posts efficiently.
* bcrypt: Safely hashes passwords for secure storage.
* Flask-SocketIO: Facilitates real-time communication between the server and clients via web sockets.
* APScheduler: Manages the scheduling of future tasks, such as post publication.
* Bootstrap: Ensures a responsive and visually pleasing frontend layout.
* Flask-Limiter: Current settings allow for basic DOS protection, where if > 50 requests are sent within a ten second period, a user is blocked for 30 seconds.

# Technologies Used (Frontend)
* Bootstrap: Provides styling and layout for a seamless user experience.
* Socket.IO: Enables bidirectional communication between server and clients, enabling features like live updates and instant messaging.

# Features:
* User Registration and Login: Secure registration with unique credentials and login functionality.
* Logout: Allows users to securely log out of their accounts.
* Post Creation: Users can create public posts with titles, descriptions, and optional image uploads.
* Scheduled Posts: Users can schedule posts for future publication, managed separately until publishing.
* Real-Time Updates: Web sockets provide instant updates for new and scheduled posts.

# Endpoints:
* GET /: Renders the login page if the user is not logged in; otherwise, redirects to the forum page.
* GET /register: Renders the registration page for new users.
* POST /register: Handles user registration form submission.
* GET /login: Renders the login page.
* POST /login: Handles user login form submission.
* POST /logout: Logs out the current user.
* POST /set_theme: Allows users to set their preferred theme for the forum.
* SocketIO Events: Manages real-time updates and interactions within the forum.

# Localhost Deployment:
1. Install Docker on your local machine.
2. Run the following command in the project directory to build and run the containers:
    * docker-compose up --build --force-recreate

# Server Deployment:
1. Set Up Deployment Variables:
    * In server.py, set the DEPLOYMENT variable to True.
    * Before deployment into production, check Flask-Limiter documentation to set up the storage_uri for limiter. Using “memory://“ is not recommended.
2. Configure Socket Connection:
    * In forum.html, modify the line:
        * Change "/" to "was://[insert domain here]" to connect to your server's domain.
3. Cloud Service Provider Setup:
    * Choose a cloud service provider (e.g., AWS, Google Cloud, DigitalOcean).
    * Set up a virtual private server (VPS) instance.
    * Install necessary dependencies (e.g., Python, MongoDB).
    * Install and configure Nginx as a reverse proxy to forward requests to your Flask application. 
    * Ensure that you have set up a way to get the IP address of the client when you reverse proxy the server (set it up using nginx)
    * In server.py, update the lines with the variable ip to get the actual IP of the client on deployment. Otherwise, every user will be affected when blocked when an excessive amount of requests is made by a user 
    * Configure firewall settings to allow traffic on ports 80 (HTTP) and 443 (HTTPS).
    * Secure your server by setting up HTTPS using SSL certificates (e.g., Let's Encrypt).
    * Deploy your Flask application using docker
    * Configure domain settings to point to your server's IP address.
    * Thoroughly test your deployment before making it live.

# Created By:
* Solomon Litvinas
* Akshay Bajpai
* Shixin Wu
* Ronny Ip
* Shreya Gupta