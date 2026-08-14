#Builder - we use this to create neccasary directories
FROM node:20.20.2-alpine3.22 As builder

# create /app and set the path to /app
WORKDIR /app

COPY package.json .

COPY *.js .

RUN npm install

# a copy /app created and After this builder will be deleted

#Final image
FROM node:20.20.2-alpine3.22

WORKDIR /app

COPY --from=builder /app /app

EXPOSE 8080

ENV MONGO_URL="mongodb://mongodb:27017/catalogue" \
    MONGO="true"

CMD ["node", "server.js"]
