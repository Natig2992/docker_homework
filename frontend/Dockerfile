#Build Stage Start

#Specify a base image
FROM node:14-alpine as builder 

#Specify a working directory
WORKDIR /app
#Copy the dependencies file
COPY package*.json ./

#Install dependencies
RUN npm install

#Copy remaining files
COPY ./ /app
#COPY . .
#COPY ./nginx.conf .
#Build the project for production
RUN npm run build 

CMD npm start

#Run Stage Start
FROM nginx:1.21
EXPOSE 80
#Copy production build files from builder phase to nginx
COPY --from=builder /app/build /usr/share/nginx/html
COPY --from=builder /app/nginx.conf /etc/nginx/conf.d/default.conf
HEALTHCHECK --interval=30s --timeout=10s --retries=3 CMD curl -sS http://127.0.0.1 || exit 1 
