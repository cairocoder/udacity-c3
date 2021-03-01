FROM node:12
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json /usr/src/app/
RUN npm ci

#Solve the problem reinstaling bcrypt
RUN npm uninstall bcrypt
RUN npm i bcrypt
RUN npm uninstall node-sass
RUN npm install node-sass

# Bundle app source
COPY . .
EXPOSE 8080
CMD [ "npm", "run", "dev" ]
