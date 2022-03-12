FROM node:14-alpine
WORKDIR /app
COPY . .
EXPOSE 3000
RUN npm install -i &&  npm run build && npm install -g serve
CMD ["serve", "-s", "build"]
