# Specify Node Version and Image
# Name Image development (can be anything)
FROM node:18.2.0 AS development

# Specify Working directory inside container
WORKDIR /api

# Copy package-lock.json & package.json from host to inside container working directory
COPY package*.json ./

# Install deps inside container
RUN npm install

COPY . .

RUN npm run build

# EXPOSE 3000

################
## PRODUCTION ##
################
# Build another image named production
FROM node:18.2.0 AS production

ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}

# Set work dir
WORKDIR /api

COPY --from=development /api/ .

EXPOSE 3000

# run app
CMD [ "node", "dist/main"]


# FROM node:18.2.0

# WORKDIR /api

# COPY package.json /api/package.json

# RUN npm install

# COPY . /api

# EXPOSE 3000

# # CMD [ "npm", "run", "start:dev" ]