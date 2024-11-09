


Node.js File System Operations & Express App with PM2 and Nginx
This repository contains two key tasks based on Node.js, Express, PM2, and Nginx:

File System Operations with Yargs: A simple Node.js application that writes to a file, checking for existing filenames.
Express Application with PM2 and Nginx: A basic Express server with a GET endpoint to return JSON data, deployed and managed with PM2 and Nginx.
Table of Contents
Task 1: File System Operations with Yargs
Task 2: Express Application with PM2 and Nginx
Contributing
License
Task 1: File System Operations with Yargs
This task demonstrates the creation of a file-writing application using the fs (file system) module and the yargs library for handling user input.

Requirements
Node.js
Yargs (npm install yargs)
Setup Instructions
Clone the repository:

bash
Copy code
git clone <repository-url>
cd <repository-folder>
Install dependencies:

bash
Copy code
npm install yargs
Usage:

Run the file-writing application with the following command:

bash
Copy code
node fileWriter.js --filename="yourFileName.txt"
If the file already exists, you will be prompted to choose a new filename.
If the file doesn't exist, it will be created with the content "You are awesome!".
Example Output:
arduino
Copy code
File "yourFileName.txt" created successfully with the message "You are awesome!"
Pushing Code to GitHub:
To upload your code to GitHub:

Initialize Git in your project folder (if not done already):

bash
Copy code
git init
Add all files:

bash
Copy code
git add .
Commit your changes:

bash
Copy code
git commit -m "Add file system operations with Yargs"
Link your GitHub repository:

bash
Copy code
git remote add origin <YOUR_GITHUB_REPO_URL>
Push your changes:

bash
Copy code
git push -u origin main
Task 2: Express Application with PM2 and Nginx
This task sets up an Express server with a GET endpoint that returns JSON data. The server is managed using PM2 and deployed with Nginx as a reverse proxy.

Requirements
Node.js
Express (npm install express)
PM2 (npm install -g pm2)
Nginx (for deployment)
Setup Instructions
Install required dependencies:

bash
Copy code
npm install express
npm install -g pm2
Create the data.json file:

This file will contain the JSON data that your server will return:

json
Copy code
{
  "message": "Hello, World!",
  "status": "success"
}
Start the Express app with PM2:

Run the application:

bash
Copy code
pm2 start app.js
To ensure the app restarts on reboot:

bash
Copy code
pm2 startup
pm2 save
Configure Nginx:

Create an Nginx configuration file for reverse proxying to the Express app:

/etc/nginx/sites-available/myapp

nginx
Copy code
server {
    listen 80;
    server_name your_domain_or_ip;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
Enable and restart Nginx:

Enable the site configuration and restart Nginx:

bash
Copy code
sudo ln -s /etc/nginx/sites-available/myapp /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
Accessing the API:
Once everything is set up, visit the following URL to get the JSON data:

bash
Copy code
http://your_domain_or_ip/data
JSON Response:
json
Copy code
{
  "message": "Hello, World!",
  "status": "success"
}
Contributing
Fork this repository.

Create your own feature branch:

bash
Copy code
git checkout -b feature-name
Commit your changes:

bash
Copy code
git commit -am 'Add feature'
Push your changes:

bash
Copy code
git push origin feature-name
Create a pull request to merge your changes.
