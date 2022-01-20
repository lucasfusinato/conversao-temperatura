FROM node:14.17.5
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 8080
RUN chown -R node /usr/src/app
USER node
CMD ["node", "server.js"]