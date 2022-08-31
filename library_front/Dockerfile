FROM node:16.17.0-alpine as builder

RUN mkdir -p /app


WORKDIR /app

ENV PATH /app/node_modules/.bin:$PATH

COPY package.json /app
COPY package-lock.json /app

RUN npm install --silent

COPY . .

RUN npm run build

FROM nginx:1.15
COPY --from=builder /app/build/ /usr/share/nginx/html

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

CMD ["nginx", "-g", "daemon off;"]
