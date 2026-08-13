FROM node:20

WORKDIR /app

COPY package.json .

COPY *.json .

RUN npm install 

EXPOSE 8080

CMD ["node", "server.js"]