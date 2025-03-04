FROM node               #Base image
WORKDIR /app            #Working directory
COPY package.json /app  #Copy package.json to /app
RUN npm install         #Install dependencies
COPY . /app             #Copy all files to /app
CMD ["node", "app.js"]  #Run the app.js file
