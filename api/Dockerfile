# Specify Node version and image
# Name image : development (can be anything)
FROM node:latest AS development

# Specify working directory inside container
WORKDIR /usr/src/app

# Copy package-lock.json & package.json from host to inside container working directory
COPY package*.json ./

# Install dep inside container
RUN npm install 

# Bundle App Sources
COPY . .

RUN npm run build

EXPOSE 3000

################################################
## PRODUCTION ##
# Build another image named production 
FROM node:alpine AS production

ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}

# Set work dir
WORKDIR /usr/src/app

COPY --from=development /usr/src/app .

EXPOSE 8080

# Run app
CMD ["node", "dist/main"]