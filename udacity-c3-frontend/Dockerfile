## Build
FROM beevelop/ionic AS ionic
# Create the application directory
WORKDIR /usr/src/app
# Install the application dependencies
# We can use wildcard to ensure both package.json AND package-lock.json are considered
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
RUN ionic build

## Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html