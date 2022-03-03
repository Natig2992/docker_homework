FROM node:14
WORKDIR /app
COPY . ./
COPY ./package.json ./
COPY ./package-lock.json ./
RUN npm install -i 
CMD ["npm", "run", "start"]
