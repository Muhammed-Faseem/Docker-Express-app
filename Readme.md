<h1>Add a Docker File</h1>

### Step 1 
Navigate to Your Node.js Project Directory:
Open a terminal (or use the integrated terminal in VS Code) and navigate to your Node.js project directory where your package.json file is located.

### Step 2
Create a Dockerfile:
Create a new file named Dockerfile in the root of your project directory. You can do this via the terminal or using a text editor.

### Step 3
Edit the Dockerfile:
Open Dockerfile with a text editor (such as VS Code) and add the following content
```
FROM node:lts-alpine
ENV NODE_ENV=production
WORKDIR /usr/src/app
COPY ["package.json", "package-lock.json*", "npm-shrinkwrap.json*", "./"]
RUN npm install --production --silent && mv node_modules ../
COPY . .
EXPOSE 3000
RUN chown -R node /usr/src/app
USER node
CMD ["npm", "start"]
```

<h1> Build the Docker Image</h1>

### Build the Docker Image:

In the terminal, navigate to your project directory (where your Dockerfile is located) and run:<br>
`docker build -t express-app .`

<h1>Run the Docker Container</h1>

### Run the Docker Container:

After building the Docker image, you can run it using: <br>
` docker run -p 3000:3000 express-app`
<br>-p 3000:\3000: Maps port 3000 on your host machine to port 3000 in the Docker container.

