FROM node:15.14-alpine

WORKDIR /app

EXPOSE 3000

COPY package.json package-lock.json ./

RUN npm install --silent

COPY . ./
RUN chmod -R 777 /app/node_modules

CMD ["npm", "start"]