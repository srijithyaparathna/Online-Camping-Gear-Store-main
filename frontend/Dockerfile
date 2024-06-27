# Use an official Node.js runtime as a parent image
FROM node:20-alpine

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Set npm registry (optional)
RUN npm config set registry https://registry.npmjs.org/

# Update npm to the latest version
RUN npm install -g npm@10.8.1

# Install dependencies with increased network timeout
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the port the app runs on
EXPOSE 3000

# Define the command to run the app
CMD ["npm", "start"]
