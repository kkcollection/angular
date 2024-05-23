# Specify Node version and image
# Name image : development (can be anything)
FROM node:latest AS development

# Specify working directory inside container
WORKDIR /usr/frontend/src/app

# Copy package-lock.json & package.json from host to inside container working directory
COPY package*.json ./

# Install dep inside container
RUN npm install 
RUN npm install -g @angular/cli

# Bundle App Sources
COPY . .

RUN npm run build

EXPOSE 4200
