FROM node:16.17.0

RUN mkdir -p /app


WORKDIR /app

ENV PATH /app/node_modules/.bin:$PATH

COPY package.json /app
COPY package-lock.json /app

RUN npm install --silent


ADD . .

CMD ["npm","start"]

EXPOSE 3000